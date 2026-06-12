---
title: "Java projects: source control and jar files"
date: 2007-11-02
forum: Programming Talk
---

### Post by meonkeys on 2007-11-02
I often want to create small, "one-off" Java projects for learning how to use a framework like, say, Hibernate, and I want to commit the project into source control for safekeeping. But Java libraries don't come standard with Ubuntu as far as I know, so, for instance, I can't just say ```
sudo apt-get install libhibernate-java
```. Anyone have an elegant solution for handling this?

My goals (in order of importance) are as follows. The solution should:
[LIST]
[*] make it quick and painless (and even fun!) for me to work with one-off projects
[*] work on the command line as well as in an IDE like Eclipse
[*] be space-efficient... I don't want to check in 100 copies of the same library, even if copies are cheap.
[*] (optional) allow projects to easily be handed to Fedora and Windows-based folks
[/LIST]

Here's all I've thought of so far:

1. commit every jar for every project into source control

(pro) guaranteed to have correct libraries
(con) huge waste of space. Hibernate 3 is over 1 megabyte, for instance

2. find or create deb packages for all libraries

(pro) libraries managed by dpkg
(con) time consuming
(con) what if I need to deploy on Fedora and the package lives in a different location than I chose?

3. leave a project's "lib" dir empty and populate as needed

(pro) don't need to check in libs
(con) time consuming

4. pick some nonstandard place to install libraries, create symlinks in my project's "lib" dir to these libraries

(pro) can work on Ubuntu, Fedora, or whatever
(pro) space-efficient
(pro) subversion can handle the symlinks
(pro) Eclipse IDE finds and uses libraries automatically
(con) need to manually set up every box I work on
(con) Windows doesn't do symlinks; can't share my example with friends using this operating system

So far I've pretty much settled on #4. What it means is I have a library directory set up like this:
```

/usr/local/lib/java
|-- bsh-2.0b4.jar
|-- bsh.jar -> bsh-2.0b4.jar
|-- hibernate-3.2.5.ga.jar
|-- hibernate3.jar -> hibernate-3.2.5.ga.jar
|-- junit-4.3.1.jar
|-- junit-4.4.jar
\-- junit.jar -> junit-4.3.1.jar

```

And here's a one-off project example:
```

.
|-- bin
|   `-- com
|       `-- example
|           |-- AppMain.class
|           `-- TestAppMain.class
|-- build.xml
|-- lib
|   |-- bsh.jar -> /usr/local/lib/bsh.jar
|   |-- hibernate3.jar -> /usr/local/lib/hibernate3.jar
|   `-- junit-4.4.jar -> /usr/local/lib/junit-4.4.jar
|-- src
|   `-- com
|       `-- example
|           `-- AppMain.java
`-- test
    `-- com
        `-- example
            `-- TestAppMain.java

```

And there you have it. Yuck, right?

---

### Post by meonkeys on 2008-11-10
One solution I've recently been turned on to is Maven. Maven is a build system that manages dependencies for you. The first time you compile a project, it will download specific versions of required software into a local repository, and other Maven-based projects can share these dependencies.

---

### Post by dribeas on 2008-11-11
> **meonkeys said:**
> ```
sudo apt-get install libhibernate-java
```. Anyone have an elegant solution for handling this?


sudo apt-get install libhibernate3-java
sudo apt-get install junit
sudo apt-get install bsh

Uhm... now that I think of it... this is a debian system. In ubuntu there are no such libs, I wonder if you can just download debian's and install the .deb...

---

