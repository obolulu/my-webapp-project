# My Webapp Project

A simple Java web application built with Maven that displays a "Hello World" landing page. This project demonstrates a basic JSP-based web application structure suitable for deployment on Apache Tomcat.

## Project Overview

This is a Maven web application project that creates a WAR (Web Application Archive) file containing a simple welcome page. The application features a clean, modern UI with a "Hello World" greeting and basic navigation buttons.

## Prerequisites

- **Java JDK** (version 8 or higher)
- **Apache Maven** (version 3.6 or higher)
- **Apache Tomcat** (version 9.0 or higher)

## Building the Project

To build the project and create the WAR file, run the following Maven command from the project root directory:

```bash
mvn clean package
```

This command will:
- Clean any previous build artifacts
- Compile the project
- Package the application into a WAR file located at `target/my-webapp-project.war`

## Deploying on Tomcat

### Option 1: Manual Deployment

1. **Copy the WAR file** to Tomcat's `webapps` directory:
   ```bash
   copy target\my-webapp-project.war <TOMCAT_HOME>\webapps\
   ```
   Or on Linux/Mac:
   ```bash
   cp target/my-webapp-project.war <TOMCAT_HOME>/webapps/
   ```

2. **Start Tomcat** (if not already running):
   ```bash
   <TOMCAT_HOME>\bin\startup.bat    # Windows
   <TOMCAT_HOME>/bin/startup.sh     # Linux/Mac
   ```

3. Tomcat will automatically extract and deploy the WAR file.

### Option 2: Using Maven Tomcat Plugin

You can also deploy directly using the Maven Tomcat plugin (if configured in `pom.xml`):

```bash
mvn tomcat7:deploy
```

## Accessing the Application Locally

Once deployed, access the application through your web browser at:

```
http://localhost:8080/my-webapp-project/
```

Or simply:

```
http://localhost:8080/my-webapp-project/index.jsp
```

**Note:** The default Tomcat port is `8080`. If your Tomcat instance uses a different port, adjust the URL accordingly.

## Project Structure

```
week1/
├── src/
│   └── main/
│       └── webapp/
│           ├── index.jsp          # Main landing page
│           ├── index.css          # Stylesheet
│           └── WEB-INF/
│               └── web.xml        # Web application deployment descriptor
├── target/                        # Build output directory
│   └── my-webapp-project.war      # Deployed WAR file
└── pom.xml                        # Maven project configuration
```

## Troubleshooting

- **Port already in use**: If port 8080 is already in use, either stop the conflicting service or configure Tomcat to use a different port in `server.xml`
- **WAR file not deploying**: Ensure Tomcat has write permissions to the `webapps` directory
- **404 Error**: Verify the WAR file was extracted correctly in the `webapps` directory and check the application context path

## Development

To run the application in development mode with hot reload, you can use:

```bash
mvn clean package
```

Then redeploy the WAR file to Tomcat. For automatic redeployment during development, consider using the Maven Tomcat plugin or an IDE with integrated Tomcat support.
