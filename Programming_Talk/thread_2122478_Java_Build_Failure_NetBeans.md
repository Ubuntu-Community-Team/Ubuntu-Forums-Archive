---
title: "Java Build Failure NetBeans"
date: 2013-03-05
forum: Programming Talk
---

### Post by KoopaTroopa on 2013-03-05
I'm not sure what may have caused this but all of a sudden when building my application netbeans says it has compiled but with errors. Continuing regardless there doesn't appear to be any problems inflicting my application but I'd like to solve the problem. Here is the output

```
run:C:\Documents and Settings\11211928\Local Settings\Application Data\NetBeans\Cache\7.3\executor-snippets\run.xml:48: 
Cancelled by user.
BUILD FAILED (total time: 3 minutes 23 seconds)
```This is on the College computer (Windows :() but are unsure if it effects netbeans on ubuntu back at home.

I've tried clearing the cache but to no avail. The 'run.xml' file in question is
```
<project name="{0} (run)" default="run" basedir=".">    <target name="run">        
        <translate-classpath classpath="${classpath}" targetProperty="classpath-translated" />//line 48
        <property name="run.jvmargs" value="" />
        <property name="work.dir" value="${basedir}"/>
        <property name="application.args" value="" />
        <java classpath="${classpath-translated}" classname="${classname}" dir="${work.dir}" jvm="${platform.java}" fork="true">
            <jvmarg value="-Dfile.encoding=${encoding}"/>
            <redirector inputencoding="${encoding}" outputencoding="${encoding}" errorencoding="${encoding}"/>
            <jvmarg line="${run.jvmargs}" />
            <arg line="${application.args}" />
            <syspropertyset>
                <propertyref prefix="run-sys-prop."/>
                <mapper from="run-sys-prop.*" to="*" type="glob"/>
            </syspropertyset>
        </java>
    </target>
</project>
```

---

### Post by varunendra on 2013-03-05
*Thread moved to **Programming Talk**.*

---

### Post by slickymaster on 2013-03-05
I see you're working with Netbeans 7.3. Did you first build and run your project with this version or on a previous version of Netbeans?

Did you tried to debug your project, in order to get some more error information?

---

### Post by KoopaTroopa on 2013-03-05
I was attempting to create another jframe in a separate test file from my jframe in the main file. As soon as I comment it out then the error no longer arises. Odd problem.

---

### Post by slickymaster on 2013-03-05
Glad you got it working.

But I really got curious about that, though. Did you get to debug it? And if so did you get an error concerning the Swing Application Framework being no longer supported?

---

