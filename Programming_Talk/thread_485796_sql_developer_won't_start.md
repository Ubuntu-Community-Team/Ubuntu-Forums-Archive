---
title: "sql developer won't start"
date: 2007-06-27
forum: Programming Talk
---

### Post by firebird84 on 2007-06-27
After I've downloaded sql developer for linux x86 from oracle, when I try to execute sqldeveloper.sh this is what I get:

```

Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.  

WARNING: error instantiating 'java.util.logging.FileHandler,' referenced by handlers, class not found
java.lang.ClassNotFoundException: java.util.logging.FileHandler,
   <<No stacktrace available>>
Exception during runtime initialization
java.lang.ExceptionInInitializerError
   <<No stacktrace available>>
Caused by: java.lang.NullPointerException
   <<No stacktrace available>>

```


Now, I've checked, and I had java jre 6 installed, and the jdk, but just for S&G I went ahead and installed jdk and jre version 5 alongside it, and still no luck =(.  This class should be included with java, and all my other apps which use java in some way seem to have no problems.  The only solution I see on google is in Russian, as well.

Just in case you don't believe me:

```
sudo aptitude search java
p   coco-java                           - Coco/R Compiler Generator (Java Version)     
p   entity-javascript                   - XML-based GUI builder for GTK+ (JavaScript bi
p   free-java-sdk                       - Complete Java SDK environment consisting of f
i   java-common                         - Base of all Java packages                    
v   java-compiler                       -                                              
i   java-gcj-compat                     - Java runtime environment using GIJ           
p   java-gcj-compat-dev                 - Java runtime environment with GCJ            
p   java-gcj-compat-plugin              - Web browser plugin to execute Java (tm) apple
p   java-package                        - utility for building Java(TM) 2 related Debia
v   java-runtime                        -                                              
v   java-virtual-machine                -                                              
v   java1-runtime                       -                                              
v   java2-compiler                      -                                              
v   java2-runtime                       -                                              
p   java2html                           - Highlight Java and C++ sources for WWW presen
p   javacc                              - A parser generator for use with Java         
p   kdebindings-java                    - KDE Java bindings metapackage                
v   lib-rxtx-java                       -                                              
p   libasm-java                         - Java bytecode manipulation framework         
p   libasm-java-doc                     - Documentation for ASM, the Java(TM) bytecode 
p   libavalon-framework-java            - Common framework for Java server applications
p   libavalon-framework-java-doc        - Documentation for Avalon framework           
p   libaxis-java                        - A SOAP implementation in Java                
p   libaxis-java-doc                    - A SOAP implementation in Java                
p   libaxis-java-gcj                    - A SOAP implementation in Java (native code)  
p   libbackport-util-concurrent-java    - backport of java.util.concurrent to Java 1.4 
i   libbcel-java                        - Analyze, create, and manipulate (binary) Java
p   libbcel-java-doc                    - Documentation for Byte Code Engineering Libra
p   libbcmail-java                      - Bouncy Castle generators/processors for S/MIM
p   libbcmail-java-doc                  - Documentation for libbcmail-java             
p   libbcmail-java-gcj                  - Bouncy Castle generators/processors for S/MIM
p   libbcpg-java                        - Bouncy Castle generators/processors for OpenP
p   libbcpg-java-doc                    - Documentation for libbcpg-java               
p   libbcpg-java-gcj                    - Bouncy Castle generators/processors for OpenP
p   libbcprov-java                      - Bouncy Castle Java Cryptographic Service Prov
p   libbcprov-java-doc                  - Documentation for libbcprov-java             
p   libbcprov-java-gcj                  - Bouncy Castle Java Cryptographic Service Prov
p   libbctsp-java                       - Bouncy Castle generators/processors for TSP  
p   libbctsp-java-doc                   - Documentation for libbctsp-java              
p   libbctsp-java-gcj                   - Bouncy Castle generators/processors for TSP  
p   libbsf-java                         - Bean Scripting Framework to support scripting
p   libbuoy-java                        - Java User Interface Toolkit                  
p   libcairo-java                       - CAIRO bindings for Java                      
p   libcairo-java-doc                   - CAIRO bindings for Java (API documentation)  
p   libcairo-java-gcj                   - CAIRO bindings for Java (native code for use 
p   libcharva1-java                     - java windowing toolkit for text terminals    
i   libcommons-beanutils-java           - utility for manipulating JavaBeans           
p   libcommons-beanutils-java-doc       - Javadoc API for libcommons-beanutils-java    
p   libcommons-cli-java                 - API for working with the command line argumen
p   libcommons-codec-java               - encoder and decoders such as Base64 and hexad
i   libcommons-collections-java         - A set of abstract data type interfaces and im
i   libcommons-collections3-java        - A set of abstract data type interfaces and im
p   libcommons-collections3-java-doc    - Documentation for libcommons-collections3-jav
p   libcommons-daemon-java              - library to launch Java applications as daemon
i   libcommons-dbcp-java                - Database Connection Pooling Services         
i   libcommons-digester-java            - Rule based XML Java object mapping tool      
p   libcommons-discovery-java           - locates classes that implement a given Java i
i   libcommons-el-java                  - Implementation of the JSP2.0 Expression Langu
p   libcommons-fileupload-java          - File upload capability to your servlets and w
p   libcommons-httpclient-java          - A Java(TM) library for creating HTTP clients 
p   libcommons-httpclient-java-doc      - Documentation for libcommons-httpclient-java 
p   libcommons-io-java                  - Common useful IO related classes             
p   libcommons-io-java-doc              - Common useful IO related classes - documentat
p   libcommons-jexl-java                - expression language engine                   
p   libcommons-jxpath-java              - manipulate javabean using XPath syntax       
p   libcommons-jxpath-java-doc          - Javadoc API for libcommons-jxpath-java       
p   libcommons-lang-java                - Extension of the java.lang package           
i   libcommons-launcher-java            - cross platform java application launcher     
i   libcommons-logging-java             - commmon wrapper interface for several logging
i   libcommons-modeler-java             - A convenience library to use Java Management 
p   libcommons-modeler-java-doc         - Javadoc API documentation and examples for Co
p   libcommons-net-java                 - internet protocol suite Java library         
i   libcommons-pool-java                - pooling implementation for Java objects      
p   libcommons-validator-java           - ease and speed development and maintenance of
p   libconcurrent-java                  - utility classes for concurrent java programmi
p   libconcurrent-java-doc              - documentation and javadoc api for libconcurre
p   libcrimson-java                     - XML parser which support the Java API for XML
p   libcrimson-java-doc                 - XML parser which support the Java API for XML
v   libdb-java                          -                                              
v   libdb-java-dev                      -                                              
p   libdb4.2-java                       - Berkeley v4.2 Database Libraries for Java    
p   libdb4.2-java-dev                   - Berkeley v4.2 Database Libraries for Java [de
p   libdb4.3-java                       - Berkeley v4.3 Database Libraries for Java    
p   libdb4.3-java-dev                   - Berkeley v4.3 Database Libraries for Java [de
p   libdb4.4-java                       - Berkeley v4.4 Database Libraries for Java    
p   libdb4.4-java-dev                   - Berkeley v4.4 Database Libraries for Java [de
p   libdb4.4-java-gcj                   - Berkeley v4.4 Database Libraries for Java (na
p   libdb4.5-java                       - Berkeley v4.5 Database Libraries for Java    
p   libdb4.5-java-dev                   - Berkeley v4.5 Database Libraries for Java [de
p   libdb4.5-java-gcj                   - Berkeley v4.4 Database Libraries for Java (na
p   libdcop3-java                       - DCOP bindings for Java                       
p   libdcop3-java-dev                   - DCOP bindings for Java (dcopidl2java program)
p   libdom1-java                        - Java bindings for the DOM API Level 1        
p   libdtdparser-java                   - Java DTD parser library                      
p   libestraier-java                    - Hyper Estraier Node API Libraries for Java   
p   libextractor-java-dev               - Java bindings for GNU libextractor (developme
p   libextractor-java0                  - Java bindings for GNU libextractor           
p   libfonts-java                       - Java fonts layouting library                 
v   libforms-java                       -                                              
v   libforms-java-doc                   -                                              
p   libgconf-java                       - LIBGCONF bindings for Java                   
p   libgconf-java-doc                   - LIBGCONF bindings for Java (API documentation
p   libgconf-java-gcj                   - LIBGCONF bindings for Java (native code for u
p   libgef-java                         - Graph Editing Framework written entirely in J
p   libgetenv-java                      - Java library for obtaining environment variab
p   libgetopt-java                      - GNU getopt - Java port                       
p   libglade-java                       - LIBGLADE bindings for Java                   
p   libglade-java-doc                   - LIBGLADE bindings for Java (API documentation
p   libglade-java-gcj                   - LIBGLADE bindings for Java (native code for u
p   libglib-java                        - GLIB bindings for Java                       
p   libglib-java-doc                    - GLIB bindings for Java (API documentation)   
p   libglib-java-gcj                    - GLIB bindings for Java (native code for use w
p   libgnome-java                       - Gnome bindings for Java                      
p   libgnome-java-doc                   - Gnome bindings for Java (native code for use 
p   libgnome-java-gcj                   - Gnome bindings for Java (native code for use 
p   libgnu-regexp-java                  - Regular Expressions for Java                 
p   libgnucrypto-java                   - full-featured cryptographic library in Java  
p   libgnuinet-java                     - extension library to provide extra network pr
p   libgnujaf-java                      - free implementation of the javabeans activati
p   libgnujmi-java                      - free implementation of the java metadata inte
p   libgnumail-java                     - free implementation of the javamail API      
p   libgtk-java                         - GTK+ bindings for Java                       
p   libgtk-java-doc                     - GTK+ bindings for Java (API documentation)   
p   libgtk-java-gcj                     - GTK+ bindings for Java (native code for use w
i   libhsqldb-java                      - Java SQL database engine                     
p   libhsqldb-java-doc                  - documentation for HSQLDB                     
p   libhsqldb-java-gcj                  - Java SQL database engine (native code)       
p   libi18n-java                        - internationalization library for java        
p   libicee-java                        - Ice-E for Java libraries                     
p   libicu4j-java                       - Library for unicode support and internalisati
p   libitext-java                       - Java Library to generate PDF on the Fly      
p   libjakarta-poi-java                 - Poor Obfuscation Implementation              
p   libjakarta-poi-java-doc             - Poor Obfuscation Implementation Documentation
p   libjama-java                        - a basic linear algebra library for java      
p   libjargs-java                       - Command-line argument parsing for Java       
p   libjargs-java-doc                   - Command-line argument parsing for Java - docu
p   libjavascript-perl                  - Perl extension for executing embedded JavaScr
p   libjavascript-rpc-perl              - Perl module to process Remote procedure calls
p   libjaxen-java                       - Java XPath engine                            
p   libjaxme-java                       - implementation of the JAXB specification for 
p   libjaxp1.2-java                     - Java XML parser and transformer APIs (DOM, SA
p   libjaxp1.2-java-gcj                 - Java XML parser and transformer APIs (DOM, SA
i   libjaxp1.3-java                     - Java XML parser and transformer APIs (DOM, SA
p   libjaxp1.3-java-gcj                 - Java XML parser and transformer APIs (DOM, SA
p   libjcalendar-java                   - Java date chooser bean for graphically pickin
p   libjcalendar-java-doc               - API documentation for libjcalendar-java      
p   libjcifs-java                       - java library for the CIFS/SMB networking prot
p   libjcifs-java-doc                   - Documentation for libjcifs-java (CIFS/SMB lib
p   libjcommon-java                     - General Purpose library for Java             
p   libjcommon-java-doc                 - General Purpose library for Java - documentat
p   libjdepend-java                     - tool to measure design quality of java class 
p   libjdom-java                        - lightweight and fast library using XML       
p   libjdom0-java                       - lightweight and fast library using XML       
p   libjdom1-java                       - lightweight and fast library using XML       
p   libjessie-java                      - free implementation of the Java Secure Socket
p   libjfreechart-java                  - Chart library for Java                       
p   libjfreechart-java-doc              - Chart library for Java - documentation       
p   libjgoodies-forms-java              - Framework to lay out and implement elegant Sw
p   libjgoodies-forms-java-doc          - Documentation for libjgoodies-forms-java     
p   libjgrapht-java                     - mathematical graph theory library for Java   
p   libjlha-java                        - LHA compress/decompress library for Java     
p   libjlha-java-doc-ja                 - Japanese documentation for libjlha-java, the 
i   libjline-java                       - Java library for handling console input      
p   libjline-java-doc                   - documentation for JLine                      
p   libjmock-java                       - Java library for testing code with mock objec
p   libjmock-java-doc                   - Java library for testing code with mock objec
i   libjsch-java                        - java secure channel                          
p   libjsch-java-doc                    - java secure channel examples                 
p   libjts-java                         - Java Topology Suite                          
p   libjts-java-doc                     - Documentation for the Java Topology Suite JTS
p   libjunitperf-java                   - JUnit extensions for performance and scalabil
p   libjunitperf-java-doc               - Documentation for libjunitperf-java          
p   libjzlib-java                       - Reimplementation of zlib in pure java        
p   libkde3-java                        - kdelibs bindings for Java                    
p   liblasso-java                       - Liberty ID-FF library - Java bindings        
i   liblog4j1.2-java                    - Logging library for java                     
p   liblog4j1.2-java-doc                - Documentation for liblog4j1.2-java           
p   liblog4j1.2-java-gcj                - Logging library for java (native code)       
p   liblogkit-java                      - Lightweight and fast designed logging toolkit
i   liblucene-java                      - full-text search engine library for Java(TM) 
i   liblucene-java-doc                  - demonstration programs and example code for L
p   libmozillainterfaces-java           - XPCOM bindings for Java                      
i   libmx4j-java                        - An open source implementation of the JMX(TM) 
p   libmx4j-java-gcj                    - An open source implementation of the JMX(TM) 
p   libmysql-java                       - Java database (JDBC) driver for MySQL        
p   libnbio2-java                       - NBIO: Nonblocking I/O for Java, Version 2    
p   libnekohtml-java                    - HTML parser for Java                         
p   libnsuml-java                       - Novosoft UML (Unified Modeling Language) libr
p   libocl-argo-java                    - Dresden OCL (Object Constraint Language) Java
p   liboro-java                         - Regular expression library for Java          
p   liboscache-java                     - High performance and widely used J2EE caching
p   libow-util-ant-tasks-java           - ObjectWeb utility Ant tasks library          
p   libpg-java                          - Java database (JDBC) driver for PostgreSQL   
p   libpgjava                           - Java database (JDBC) driver for PostgreSQL - 
p   libpixie-java                       - Java Vector Format Viewer Library            
p   libpng-sixlegs-java                 - Java package to read and display PNG images  
p   libpostgis-java                     - geographic objects support for PostgreSQL -- 
p   libqdbm-java                        - QDBM Database Libraries for Java             
p   libqt3-java                         - Java bindings for Qt                         
p   libreadline-java                    - GNU readline and BSD editline wrappers for Ja
p   libreadline-java-doc                - API docs for readline/editline wrappers for J
i   libregexp-java                      - regular expression library for Java          
p   librelaxng-datatype-java            - Datatype interfaces for Relax NG             
p   librxtx-java                        - Full Java CommAPI implementation             
p   libsablevm-classlib1-java           - GNU Classpath modified to work with SableVM J
p   libsapdbc-java                      - JDBC interface to the MaxDB database system  
p   libsaxon-java                       - The Saxon XSLT Processor                     
p   libsaxon-java-doc                   - The Saxon XSLT Processor's documentation and 
p   libsaxpath-java                     - Java XPath engine for use on a variety of XML
p   libseda-java                        - the Staged Event-Driven Architecture library 
i   libservlet2.3-java                  - Servlet 2.3 and JSP 1.2 Java classes and docu
i   libservlet2.4-java                  - Servlet 2.4 and JSP 2.0 Java classes and docu
p   libservlet2.4-java-gcj              - Servlet 2.4 and JSP 2.0 Java classes and docu
p   libslide-webdavclient-java          - WebDAV client library for Java               
p   libsnmp1.4-java                     - Open Source implementation of the SNMP protoc
p   libsqlrelay-java                    - SQL Relay Java API                           
p   libstruts1.2-java                   - Java Framework for MVC web applications      
p   libsvn-java                         - Java bindings for Subversion                 
p   libsvn-javahl                       - Java bindings for Subversion (dummy package) 
i   libswt3.2-gtk-java                  - Fast and rich GUI toolkit for Java, gtk2 vers
p   libtomcat5-java                     - Java Servlet engine -- core libraries        
i   libtomcat5.5-java                   - Java Servlet engine -- core libraries        
p   libtoolbar-java                     - extension of java swing component JToolBar   
p   libvecmath1.2-java                  - implementation of javax.vecmath package from 
p   libvte-java                         - VTE bindings for Java                        
p   libvte-java-doc                     - VTE bindings for Java (API documentation)    
p   libvte-java-gcj                     - VTE bindings for Java (native code for use wi
p   libwerken.xpath-java                - JDOM XPath Engine                            
p   libwsdl4j-java                      - Webservice description language for Java     
p   libwsdl4j-java-doc                  - Documentation for Java Web Services Library  
i   libxalan2-java                      - XSL Transformations (XSLT) processor in Java 
p   libxalan2-java-doc                  - Documentation and examples for the Xalan-Java
p   libxalan2-java-gcj                  - XSL Transformations (XSLT) processor in Java 
p   libxerces-java                      - Validating XML parser for Java               
i   libxerces2-java                     - Validating XML parser for Java with DOM level
p   libxerces2-java-gcj                 - Validating XML parser for Java with DOM level
p   libxml-commons-resolver1.1-java     - XML entity and URI resolver library          
p   libxml-commons-resolver1.1-java-doc - XML entity and URI resolver library -- docume
p   libxml-im-exporter-java             - Java library for handling XML documents      
p   libxp-java                          - XML 1.0 parser for Java                      
p   libxpp2-java                        - XML pull parser library for java V2          
p   libxpp3-java                        - XML pull parser library for java             
p   libxsltc-java                       - XSL Transformations (XSLT) compiler from Xala
p   libxsltc-java-gcj                   - XSL Transformations (XSLT) compiler from Xala
p   libxt-java                          - An implementation in Java of XSL Transformati
p   libxt-java-gcj                      - An implementation in Java of XSL Transformati
p   libzeroc-ice-java                   - Ice for Java libraries                       
p   monodevelop-java                    - Java plugin for MonoDevelop                  
v   openoffice.org-java                 -                                              
i   openoffice.org-java-common          - OpenOffice.org office suite Java support arch
v   openoffice.org2-java-common         -                                              
v   postgresql-8.1-pljava               -                                              
p   postgresql-8.1-pljava-gcj           - Java procedural language for PostgreSQL      
p   slice2java                          - Slice to Java translator                     
p   slice2javae                         - Slice to Java translator for IceE            
i   sun-java5-bin                       - Sun Java(TM) Runtime Environment (JRE) 5.0 (a
i   sun-java5-demo                      - Sun Java(TM) Development Kit (JDK) 5.0 demos 
p   sun-java5-doc                       - Sun JDK(TM) Documention -- integration instal
p   sun-java5-fonts                     - Lucida TrueType fonts (from the Sun JRE)     
i   sun-java5-jdk                       - Sun Java(TM) Development Kit (JDK) 5.0       
i   sun-java5-jre                       - Sun Java(TM) Runtime Environment (JRE) 5.0 (a
p   sun-java5-plugin                    - The Java(TM) Plug-in, Java SE 5.0            
p   sun-java5-source                    - Sun Java(TM) Development Kit (JDK) 5.0 source
i   sun-java6-bin                       - Sun Java(TM) Runtime Environment (JRE) 6 (arc
p   sun-java6-demo                      - Sun Java(TM) Development Kit (JDK) 6 demos an
p   sun-java6-doc                       - Sun JDK(TM) Documention -- integration instal
p   sun-java6-fonts                     - Lucida TrueType fonts (from the Sun JRE)     
p   sun-java6-javadb                    - Java(TM) DB, Sun Microsystems' distribution o
i   sun-java6-jdk                       - Sun Java(TM) Development Kit (JDK) 6         
i   sun-java6-jre                       - Sun Java(TM) Runtime Environment (JRE) 6 (arc
p   sun-java6-plugin                    - The Java(TM) Plug-in, Java SE 6              
p   sun-java6-source                    - Sun Java(TM) Development Kit (JDK) 6 source f
p   tightvnc-java                       - TightVNC java applet and command line program
p   vnc-java                            - VNC java applet and command line program     
p   wipl-client-java                    - A client for wipl-daemon, usable through a we

```

Anyone have any idea why I can't start it?

---

### Post by Cirdes Borges on 2007-06-27
I'm with the same problem and until now no solutions

---

### Post by macdum on 2007-06-28
Check your environment variables 

make sure JAVA_HOME  is set

type 'evn' to see your environment variables, if its not there add it: 

export JAVA_HOME=<path to jdk>/jdk1.5.0_12

---

### Post by thiaggodiniz on 2007-06-28
i set the variable and the sql developer did opened, but inside the frame nothig showed up.
in oracle's site it recomends jre 1.5, i have 1.6. is this the problem?

---

### Post by firebird84 on 2007-07-02
If you're using Beryl - don't.  I think java/swing has issues with it.

---

### Post by firebird84 on 2007-07-02
> **macdum said:**
> Check your environment variables 

make sure JAVA_HOME  is set

type 'evn' to see your environment variables, if its not there add it: 

export JAVA_HOME=<path to jdk>/jdk1.5.0_12

By the way, thanks! That worked.  I'm not sure why I never tried it myself...

---

### Post by bated_breath on 2007-07-02
You could do the following:

```
gedit <sql-devloper-install-directory>/jdev/bin/ide.conf
```

(replace <sql-devloper-install-directory> with the path to your install)

add the following lines to the ide.conf file:

> 
SetJavaHome /usr/lib/j2sdk1.5-sun
SetSkipJ2SDKCheck true
 

By doing it this way it means that you can point sql developer at a different java environment to what you use day-to-day.

---

### Post by bmw330i on 2007-09-11
Hey all,

Nothing listed here worked completely. JAVA_HOME did need to be set but not until after I (synaptic package manager) installed EVERYTHING in the jdk6 find list for jdk

All that needs to be done is install enough of the JDK6 in Synaptic Package Manager, then set the JAVA_HOME env variable before executing the sqldeveloper binary.

My exact steps (read all of them before starting; and after downloading the sqldeveloper binaries to a location):
1. Open Synaptic Package Manager
2. search for "jdk" or "sun-java6" maybe better.
3. checked to install: sun-java6-bin, sun-java6-demo, sun-java6-doc, sun-java6-javadb, sun-java6-jdk, sun-java6-jre, sun-java6-source (I admit likely you don't need everything)
4. the terminal complained it needed a root owned file in /tmp named: jdk-6-doc.zip and that you download it from: [https://sdlc3b.sun.com/ECom/EComActi...1C41166F3C41F7](https://sdlc3b.sun.com/ECom/EComActi...1C41166F3C41F7)
or
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) and click the "Documentation" button, accept lic. agreement, download it to /tmp/
I suggest do the download to tmp first chown to root then do step 1 above.and avoid this issue.
5. after finished installing exit S.P.M.
6. export JAVA_HOME=/opt/SDK/jdk
7. I put my sqldeveloper in /usr/local/share so my command is:
"/usr/local/share/sqldeveloper/sqldeveloper/bin/sq ldeveloper"
NOTE: there is a sqldeveloper.sh script that for me doesn't work so I am calling the binary directly. I suggest creating a symlink to it in /usr/local/bin
"ln -s /usr/local/share/sqldeveloper/sqldeveloper/bin/sql developer /usr/local/bin/sqldeveloper"

At this point I launch it with:
"export JAVA_HOME=/opt/SDK/jdk; sqldeveloper"

Works for me...hope this helps anyone who didn't find the above worked like me.

-D

---

### Post by rubyflux on 2008-01-07
I had the problem with the blank pane appearing - disabling desktop effects (Beryl or otherwise) fixed the problem. I actually had desktop effects on with SQLDeveloper running with a blank pane, turned desktop effects off and the SQLDeveloper pane redrew itself correctly, no restart needed. I guess it is something about effects that makes Swing cranky.

---

### Post by psr_177 on 2008-03-12
Hi,
I have ubuntu Ls6.06 and trying to install Sql Developer.
Initially I got this error:
psr@psr-laptop:~/Desktop/jdk1.6.0_05/bin$ cd ..
psr@psr-laptop:~/Desktop/jdk1.6.0_05$ cd ..
psr@psr-laptop:~/Desktop$ cd sqldeveloper
psr@psr-laptop:~/Desktop/sqldeveloper$ sh sqldeveloper.sh

Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.

Error: This product requires a Java(TM) Platform 5.0 runtime.
You are using 1.4.2 from /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre
_______________________
:mad:
But I have installed Java JDK5 update from Sun java website and used the follwing link for installation document:
[http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html#troubleshooting](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html#troubleshooting)

As shown below java was installed
psr@psr-laptop:~/Desktop/jdk1.6.0_05$ ls
bin        db    include  lib      man          README_ja.html     register.html     register_zh_CN.html  src.zip
COPYRIGHT  demo  jre      LICENSE  README.html  README_zh_CN.html  register_ja.html  sample               THIRDPARTYLICENSEREADME.txt
psr@psr-laptop:~/Desktop/jdk1.6.0_05$ cd bin
psr@psr-laptop:~/Desktop/jdk1.6.0_05/bin$ ls
appletviewer  HtmlConverter  java     javap         jcontrol  jmap        jstack   native2ascii  rmic         serialver   wsgen
apt           idlj           javac    java-rmi.cgi  jdb       jps         jstat    orbd          rmid         servertool  wsimport
ControlPanel  jar            javadoc  javaws        jhat      jrunscript  jstatd   pack200       rmiregistry  tnameserv   xjc
extcheck      jarsigner      javah    jconsole      jinfo     jsadebugd   keytool  policytool    schemagen    unpack200


But still I am getting the same error 

Oracle SQL Developer
 Copyright (c) 2006, 2007, Oracle. All rights reserved.

Error: This product requires a Java(TM) Platform 5.0 runtime.
You are using 1.4.2 from /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre
_______________________
:confused:

Any help please...

---

