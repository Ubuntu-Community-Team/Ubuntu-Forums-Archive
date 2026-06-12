---
title: "How To Install/Compile Jotify and JOrbis"
date: 2014-05-19
forum: Packaging and Compiling Programs
---

### Post by Virus666 on 2014-05-19
Hi all,

I know, that's an out dated software but I'd like to give a try. I am trying to install **Jotify** (Java fork of **Despotify**) but encountering some dependency problems. I have installed **gradle** and its dependencies via Synaptic. However when I tried to install Jotify via "gradle jar" command, the installation suspends due to lack of **JOrbis**. Installing **libjorbis-java**, **libcortado-java**, **cortado**, **libvorbisspi-java** packages via Synaptic did not help.

Website of Jotify and JOrbis:

[https://github.com/jkwatson/jotify](https://github.com/jkwatson/jotify)
[http://www.jcraft.com/jorbis/](http://www.jcraft.com/jorbis/)

The output that I got:

```
~/jotify-master $ gradle jar
:commons:compileJava
:: problems summary ::
:::: WARNINGS
        module not found: jorbis#jorbis;0.0.17

    ==== clientModule: tried

    ==== internal-repository: tried

    ==== MavenRepo: tried

      http://repo1.maven.org/maven2/jorbis/jorbis/0.0.17/jorbis-0.0.17.pom

      -- artifact jorbis#jorbis;0.0.17!jorbis.jar:

      http://repo1.maven.org/maven2/jorbis/jorbis/0.0.17/jorbis-0.0.17.jar

    ==== http://openccdb.org:8081/nexus/content/repositories/thirdparty/: tried

      http://openccdb.org:8081/nexus/content/repositories/thirdparty/jorbis/jorbis/0.0.17/jorbis-0.0.17.pom

      -- artifact jorbis#jorbis;0.0.17!jorbis.jar:

      http://openccdb.org:8081/nexus/content/repositories/thirdparty/jorbis/jorbis/0.0.17/jorbis-0.0.17.jar

        ::::::::::::::::::::::::::::::::::::::::::::::

        ::          UNRESOLVED DEPENDENCIES         ::

        ::::::::::::::::::::::::::::::::::::::::::::::

        :: jorbis#jorbis;0.0.17: not found

        ::::::::::::::::::::::::::::::::::::::::::::::


:::: ERRORS
    Server access Error: Connection refused url=http://openccdb.org:8081/nexus/content/repositories/thirdparty/jorbis/jorbis/0.0.17/jorbis-0.0.17.pom

    Server access Error: Connection refused url=http://openccdb.org:8081/nexus/content/repositories/thirdparty/jorbis/jorbis/0.0.17/jorbis-0.0.17.jar


FAILURE: Build failed with an exception.

* What went wrong:
Could not resolve all dependencies for configuration ':commons:compile':
    - unresolved dependency: jorbis#jorbis;0.0.17: not found


* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 7.179 secs
```

Any ideas? Thanks.

---

### Post by oldos2er on 2014-05-19
Moved to Packaging & Compiling Programs.

---

