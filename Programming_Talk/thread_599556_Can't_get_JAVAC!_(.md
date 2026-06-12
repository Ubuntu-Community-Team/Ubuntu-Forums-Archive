---
title: "Can't get JAVAC! :("
date: 2007-11-01
forum: Programming Talk
---

### Post by Prolog on 2007-11-01
Hey everyone. All I want to do is get the java compiler (javac) working on my linux (Ubuntu Dapper 6.06)... HOWEVER... everytime I try to sudo apt-get install sun-java5-jdk on the cmd line of the terminal I get the following:

"Reading package lists... Done"
"Building dependency tree... Done"
"E: Couldn't find package sun-java5-jdk"

And that's it! I can't seem to get javac on my linux for the life of me and I have a project coming up which I would like to be able to program at home on my own computer and not always at the campus labs.

I hope someone can help, this is really getting annoying! :mad:

Thanks in advance!
-SP

---

### Post by nanotube on 2007-11-01
have you enabled the multiverse repository?

what version of ubuntu are you running? (sun java wasn't in the repos prior to... feisty, i think)

also, why get java5 instead of java6? :)

---

### Post by LaRoza on 2007-11-01
Look at what available in the GUI Synaptic and Add/Remove Programs

---

### Post by Prolog on 2007-11-01
I have tried Synaptic to no avail and I dont even know what the multiverse repository is! I am running Dapper.. and im not sure how to upgrade even really. It doesint matter what version of java I get.. I just want to be able to compile my code!!!!!!!!!

SOMEONE HELP!!!!!!! :(

---

### Post by Engnome on 2007-11-01
> **Prolog said:**
> I have tried Synaptic to no avail and I dont even know what the multiverse repository is! I am running Dapper.. and im not sure how to upgrade even really. It doesint matter what version of java I get.. I just want to be able to compile my code!!!!!!!!!

SOMEONE HELP!!!!!!! :(

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by LaRoza on 2007-11-01
[http://packages.ubuntu.com/dapper/devel/sun-java5-jdk](http://packages.ubuntu.com/dapper/devel/sun-java5-jdk)

I hope that helps.

---

### Post by Prolog on 2007-11-02
> **Prolog said:**
> I have tried Synaptic to no avail and I dont even know what the multiverse repository is! I am running Dapper.. and im not sure how to upgrade even really. It doesint matter what version of java I get.. I just want to be able to compile my code!!!!!!!!!

SOMEONE HELP!!!!!!! :(

TY! This helped me fix my issue. Thanks so much. :)

---

### Post by LaRoza on 2007-11-02
> **Prolog said:**
> TY! This helped me fix my issue. Thanks so much. :)

Who helped?

(Mark this as soved, if it is)

---

### Post by t1kky on 2008-02-29
Hi , I have a similar problem. I reinstalled several versions of java form 1.4 tu sun-java6-* but none can supply me with javac. it keeps showing me this:
The program 'javac' can be found in the following packages:
 * jikes-sun
 * jikes-sablevm
 * kaffe
 * sun-java6-jdk
 * jikes-classpath
 * java-gcj-compat-dev
 * ecj
 * j2sdk1.4
 * jikes-gij
 * jikes-kaffe
 * sun-java5-jdk
 * gcj-4.1
Try: sudo apt-get install <selected package>
bash: javac: command not found
Fine and dandy but i've installed every each of em and stil no javac to use.
:confused:

---

### Post by LaRoza on 2008-02-29
Enable all repositories, run:

```

sudo aptitude install sun-java6-jdk

```

---

### Post by t1kky on 2008-02-29
thanks a lot mate !:)

---

### Post by iamdennisthomas on 2008-04-13
well i face the same problem every morning. i dont have the permenant solution to it but the temporary one is the javac is not in the path. so everytime u type javac it is not recognised. just try saving the jdk folder as the path and also give its java home path. This will do until u reboot ur computer.

---

### Post by iamdennisthomas on 2008-04-13
or else u download the new java version. well that is recommended becuase then it will also reduce ur work when u install new develeopment tools like eclipse as it automatically fetches ur jdk version

---

