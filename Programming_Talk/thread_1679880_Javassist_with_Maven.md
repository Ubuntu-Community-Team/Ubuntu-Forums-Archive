---
title: "Javassist with Maven"
date: 2011-02-01
forum: Programming Talk
---

### Post by pcman312 on 2011-02-01
I'm trying to do some byte code manipulation with Javassist using Maven. I keep getting a compilation error:
```
[pathToTheFile]:[59,18] cannot access com.sun.jdi.connect.IllegalConnectorArgumentsException
class file for com.sun.jdi.connect.IllegalConnectorArgumentsException not found
		HotSwapper hs = new HotSwapper(debugPort);
```

It's as if the JDK is missing a class file. I have the sun JDK installed and I know that maven is using it because when I do a mvn -v call it gives me this (I'm using Ubuntu by the way):
```
Apache Maven 2.2.1 (rdebian-1)
Java version: 1.6.0_22
Java home: /usr/lib/jvm/java-6-sun-1.6.0.22/jre
Default locale: en_US, platform encoding: UTF-8
OS name: "linux" version: "2.6.31-22-generic" arch: "amd64" Family: "unix"
```

I have this as my pom file (this is currently just a test project to make sure that I can get everything set up correctly):
```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>

   <groupId>test-bytecode</groupId>
   <artifactId>test-bytecode</artifactId>
   <version>0.0.1-SNAPSHOT</version>
   <packaging>jar</packaging>

   <name>test-bytecode</name>
   <url>http://maven.apache.org</url>

   <properties>
      <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
   </properties>

   <dependencies>
      <dependency>
         <groupId>junit</groupId>
         <artifactId>junit</artifactId>
         <version>4.8.1</version>
         <scope>test</scope>
      </dependency>
      <dependency>
         <groupId>javassist</groupId>
         <artifactId>javassist</artifactId>
         <version>3.9.0.GA</version>
         <scope>test</scope>
      </dependency>
   </dependencies>

   <build>
      <plugins>
         <plugin>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>2.0</version>
            <configuration>
               <optimize>true</optimize>
               <source>6</source>
               <target>6</target>
            </configuration>
         </plugin>
         <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>2.7.2</version>
            <configuration>
               <argLine>-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005</argLine>
            </configuration>
         </plugin>
      </plugins>
   </build>
</project>
```

Any ideas on how to fix this problem?

---

### Post by pcman312 on 2011-02-01
Turns out it wasn't loading the tools.jar library in the jdk lib folder. I added this to the pom file and it worked:

```
<dependency>
	<groupId>sun.jdk</groupId>
	<artifactId>tools</artifactId>
	<version>1.5.0</version>
	<scope>system</scope>
	<systemPath>${java.home}/../lib/tools.jar</systemPath>
</dependency>
```

---

### Post by pcman312 on 2011-02-01
I should note that this solution apparently doesn't work on mac's. We've replaced the dependency with a profile instead:

```
<profiles>
	<profile>
		<id>default-tools.jar</id>
		<activation>
			<property>
				<name>java.vendor</name>
				<value>Sun Microsystems Inc.</value>
			</property>
		</activation>
		<dependencies>
			<dependency>
				<groupId>com.sun</groupId>
				<artifactId>tools</artifactId>
				<version>1.5.0</version>
				<scope>system</scope>
				<systemPath>${java.home}/../lib/tools.jar</systemPath>
			</dependency>
		</dependencies>
	</profile>
</profiles>
```

---

