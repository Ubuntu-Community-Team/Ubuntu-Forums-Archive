---
title: "WebSVN under Tomcat on Kubuntu 6.06"
date: 2006-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by leo_m on 2006-07-01
WebSVN is a PHP based client to view repository information and generate reports over HTTP.
[http://websvn.tigris.org/](http://websvn.tigris.org/)

PHP-Java-bridge provides you a few methods of java-php interaction. One of those methods is deploying PHP-Java-bridge as a web-application and deploy your PHP files in that web-application.
[http://php-java-bridge.sourceforge.net/](http://php-java-bridge.sourceforge.net/)

PHP is available from [http://php.net](http://php.net) and is used by php-java-bridge and websvn.

Note that you will need subversion executable to be installed on your system - it is required by WebSVN.  It is pointless to use WebSVN without Subversion in any case; and WebSVN needs to be installed on the computer where the repository is installed; so that system must have Subversion executable as well as the Subversion repository - WebSVN uses svnlook and svn.

Okay, get PHP source, WebSVN (I used version 1.61) and php-java-bridge and expand these into different folders.
 
 The bridge supports some major servers through modules, other servers are supported through CGI implementation. The bridge uses fastcgi on Linux/Unix if your php binary supports that.

However, the default php binary supplied with java-php bridge OR Ubuntu 6.06 does not have pcre-regex support, but WebSVN application needs that. So, php has to be built again with the said module for the targeted architecture/s.

As an example, I did this on my local system (after downloading PHP source from web-site mentioned above and expanding it into a folder and navigating to that folder), having Ubuntu on i686, using...
```

./configure --prefix=/home/leo/php-5.1.4.dist --disable-all --enable-fastcgi --enable-pcre-regex --with-pcre-regex --with-fastcgi
make
make install

``` 
Then I copied over the php binary to the java-php-bridge's WEB-INF/cgi folder under the same name as the existing php binary for my platform (x86), replacing that file (you can rename that intead of replacing). The path in web.xml should point to a php binary with pcre-regex support. Alternatively (a better approach) is to put the php binary directly under WEB-INF/cgi folder, replacing the binary supplied with java-php-bridge.

For performance reasons, the java-php-bridge by default attempts to use fastcgi in CGI-type deployments (e.g., for jboss/tomcat, where separate modules are not used), so it helps if the php binary is compiled with fastcgi support.

You may wish to configure sockets for fastcgi support, particularly if there is any instance in future when multiple installations of java-php-bridge are to be supported on the same machine. For the default behaviour of php-java-bridge (may suffice for a single installation), kindly refer to the web.xml file, commented out sections in the websvn deployment with java-php-bridge.

Since the PHP binary is deployed under WEB-INF (WEB-INF/cgi) folder, it is not accessible for direct invocation by any malicious users.

Those having Ant support can use the following instructions (download Ant from [http://ant.apache.org/]("http://ant.apache.org/%29:") )

I assume you downloaded and expanded php-java-bridge in the php-java-bridge folder.

I assume you downloaded and expanded websvn in the websvn folder (not in a sub-folder under this folder, e.g., I mean, NOT under websvn/websvn-1.6.1 - the same comment applies to php-java-bridge also, e.g., I do NOT expect you to expand php-java-bridge under php-java-bridge/php-java-bridge-3.1.1_j2ee).

Place the following Ant script in the folder under which the php-java-bridge and websvn folders are available, name it build.xml (before running this Ant script, make sure you do not have folders named build or dist in the folder where you placed the build.xml - they will be wiped out):
[NB: I use folders to mean directories, and vice-versa - places where you keep other files and folders/directories]

```

<?xml version="1.0"?>
<!-- ====================================================================== 
     WebSVN build    
     Creates WebSVN web-app (combined with PHP-Java-Bridge)
                   
     leo_m                                                                
     ====================================================================== -->
<project name="websvn" default="dist" basedir=".">
    <description>Build file for WebSVN</description>

    <property name="php-integration.src" location="php-java-bridge"/>
    <property name="websvn.src" location="websvn"/>

    <!-- - - - - - - - - - - - - - - - - - 
          target: clean                      
         - - - - - - - - - - - - - - - - - -->
    <target name="clean">
        <delete includeEmptyDirs="true">
            <fileset dir=".">
                <include name="dist/**" />
                <include name="build/**" />
            </fileset>
        </delete>
    </target>

    <!-- - - - - - - - - - - - - - - - - - 
          target: php-integrate                      
         - - - - - - - - - - - - - - - - - -->
    <target name="php-integrate">
        <mkdir dir="build" />
        <loadproperties srcfile="file_paths.properties" />
        <!-- file_paths.properties contents, create in the same directory as this build file, modify appropriately:
# PHP paths
windows.php.path=C:\\PHP\\php-cgi.exe
unix.php.path=/usr/bin/php
# SVN paths
windows.svn.path=C:\\Subversion\\bin
unix.svn.path=/usr/bin/
# Data Repository paths
windows.data.path=C:\\SubversionRepos\\data
unix.data.path=/data/subversion/repositories/repo        
        -->
        <exec executable="which" os="Linux, Unix" outputproperty="php_executable_path" failifexecutionfails="no" failonerror="false">
            <arg line="php" />
        </exec>
        <exec executable="which" os="Linux, Unix" failifexecutionfails="no" failonerror="false">
            <arg line="svn" />
            <redirector outputproperty="svn_executable_path" append="false">
                <outputfilterchain>
                    <tokenfilter>
                        <stringtokenizer/>
                        <replaceregex pattern="(.*)/svn(.*)" replace="\1"/>
                    </tokenfilter>    
                </outputfilterchain>
            </redirector>
        </exec>
        <condition property="DoDefaultCopy">
            <and>
                <isset property="php_executable_path" />
                <isset property="svn_executable_path" />
            </and>
        </condition>
        <antcall target="attempt_default_copy" />


        <!-- read from the properties file if either of *which* commands (for svn and php) failed -->
        <condition property="DoWindowsCopy">
            <and>
                <os family="Windows" />
                <or>
                    <not>
                        <isset property="php_executable_path" />
                    </not>
                    <not>
                        <isset property="svn_executable_path" />
                    </not>
                </or>
            </and>
        </condition>
        <antcall target="attempt_windows_copy" />

        <condition property="DoUnixCopy">
            <and>
                <os family="Unix" />
                <or>
                    <not>
                        <isset property="php_executable_path" />
                    </not>
                    <not>
                        <isset property="svn_executable_path" />
                    </not>
                </or>
            </and>
        </condition>
        <antcall target="attempt_unix_copy" />
    </target>

    <!-- - - - - - - - - - - - - - - - - - 
          target: attempt_default_copy                      
         - - - - - - - - - - - - - - - - - -->
    <target name="attempt_default_copy" if="DoDefaultCopy">
        <echo message="The PHP executable found using *which* command is ${php_executable_path}" />
        <echo message="The SVN executable found using *which* command is ${svn_executable_path}" />
        <!-- oh, there is no straightforward command to deduce the repository path, assuming unix -->
        <property name="svn_repository_path" value="${unix.data.path}" />
        <antcall target="replace_tokens" />
    </target>

    <!-- - - - - - - - - - - - - - - - - - 
          target: attempt_windows_copy                      
         - - - - - - - - - - - - - - - - - -->
    <target name="attempt_windows_copy" if="DoWindowsCopy">
        <property name="php_executable_path" value="${windows.php.path}" />
        <property name="svn_executable_path" value="${windows.svn.path}" />
        <property name="svn_repository_path" value="${windows.data.path}" />
        <echo message="The PHP executable is ${php_executable_path}" />
        <echo message="The SVN executable is ${svn_executable_path}" />
        <antcall target="replace_tokens" />
    </target>

    <!-- - - - - - - - - - - - - - - - - - 
          target: attempt_unix_copy                      
         - - - - - - - - - - - - - - - - - -->
    <target name="attempt_unix_copy" if="DoUnixCopy">
        <property name="php_executable_path" value="${unix.php.path}" />
        <property name="svn_executable_path" value="${unix.svn.path}" />
        <property name="svn_repository_path" value="${unix.data.path}" />
        <echo message="The PHP executable is ${php_executable_path}" />
        <echo message="The SVN executable is ${svn_executable_path}" />
        <antcall target="replace_tokens" />
    </target>


    <!-- - - - - - - - - - - - - - - - - - 
          target: replace_tokens                      
         - - - - - - - - - - - - - - - - - -->
    <target name="replace_tokens" if="php_executable_path">
        <copy todir="build/src">
            <fileset dir="${websvn.src}">
                <exclude name="include/config.inc" />
            </fileset>
            <!-- we do not copy index.php from php-java-bridge, we keep the websvn .php versions, 
                    there are no other files with same name existing in both websvn and php-java-bridge -->
            <fileset dir="${php-integration.src}">
                <exclude name="WEB-INF/web.xml" />
                <exclude name="index.php" />
            </fileset>
        </copy>
        <copy todir="build/src">
            <fileset dir="${websvn.src}">
                <include name="include/config.inc" />
            </fileset>
            <filterchain>
                <filterreader classname="org.apache.tools.ant.filters.ReplaceTokens">
                    <param type="token" name="SVN_EXECUTABLE_PATH" value="${svn_executable_path}" />
                    <param type="token" name="SVN_REPOSITORY_PATH" value="${svn_repository_path}" />
                </filterreader>
            </filterchain>
        </copy>
        <copy todir="build/src">
            <fileset dir="${php-integration.src}">
                <include name="WEB-INF/web.xml" />
            </fileset>
            <filterchain>
                <filterreader classname="org.apache.tools.ant.filters.ReplaceTokens">
                    <param type="token" name="PHP_EXECUTABLE_PATH" value="${php_executable_path}" />
                    <param type="token" name="SVNPATH" value="${svnpath}" />
                </filterreader>
            </filterchain>
        </copy>
    </target>

    <!-- dependency upon homedeck_auth build, a few other dependencies - read this target fully -->
    <!-- it is assumed that websvn will be deployed under the same (CAPS) server as homedeck editor,
            so that it will have access to other libs on which it is dependent (log4j, tm* classes)
            - these are required by authentication filter, not websvn as such -->
    <target name="dist" depends="clean,php-integrate">
        <mkdir dir="dist" />
        <war destfile="dist/websvn.war" webxml="build/src/WEB-INF/web.xml" duplicate="fail">
            <fileset dir="build/src">
                <exclude name="WEB-INF/**" />
                <exclude name="META-INF/**" />
            </fileset>

            <metainf dir="build/src/META-INF" />

            <webinf dir="build/src/WEB-INF">
                <exclude name="web.xml" />
                <exclude name="lib/**" />
            <!-- <exclude name="classes/**" /> -->
            </webinf>

            <lib dir="build/src/WEB-INF/lib" />

            <!-- <classes dir="build/src/WEB-INF/classes">
                <include name="**/*.class" />
            </classes> -->
        </war>
    </target>

</project>

``` 
Copy the following contents in a file named file_paths.properties in the same folder as your build.xml Ant script, modify it to suit paths in your setup:

```

# PHP paths
windows.php.path=C:\\PHP\\php-cgi.exe
unix.php.path=/usr/bin/php
# SVN paths
windows.svn.path=C:\\Subversion\\bin
unix.svn.path=/usr/local/bin/
# Data Repository paths
windows.data.path=C:\\SubversionRepos\\data
unix.data.path=/data/subversion/repositories/repo

``` 
Run the Ant script.  It will create the websvn.war in the folder named dist.

WebSVN and php-java-bridge have the file index.php in common; we delete php-java-bridge's version and keep WebSVN's index.php.  There are no other overlaps (besides perhaps the manifest file) as of this writing; note that we want the WebSVN versions to ovewrite the php-java-bridge PHP files in case of conflicts in PHP file-names - we are using php-java-bridge for its servlet/s.

As noted in the beginning of this post, after deploying the websvn.war file, when it gets expanded into a folder, you should put the proper PHP binary in the WEB-INF/cgi folder; otherwise WebSVN will complain (unless you chose to point to an existing PHP binary with pcre-regex support in WEB-INF/web.xml).

If you already have a PHP with pcre-regex support on your system, just uncomment the line pointing to that file in the WEB-INF/web.xml file and you are ready to go (in this case, you need not replace the PHP binary for your platform in WEB-INF/cgi).

Those who are running AMD64 and choose to place the PHP binary in WEB-INF/cgi, should create a script in WEB-INF/cgi named php-cgi-amd64-linux.sh - adapt another script in WEB-INF/cgi after putting the appropriate PHP binary in WEB-INF/cgi.

---

