---
title: "error installing jre for linux"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by captain_buckethead on 2008-11-06
Hey all

when I was installing Java Runtime environment for linux (32 bit), I was confronted with the below listed error message:

```

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./jre-6u10-linux-i586.bin: 363: ./install.sfx.10279: not found

Done.
glenn@glenn1:/usr/java$ ls
jre1.6.0_10  jre-6u10-linux-i586.bin

```

Does anyone know what happened and how I can make this install work?

Glenn.

---

### Post by taurus on 2008-11-06
Any reason you don't want to install the version from the repos?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by bobnutfield on 2008-11-06
Did you run the .bin script (sh jre-6u10-linux-i586.bin) as sudo?

---

### Post by afzal_du on 2008-11-21
I've also downloaded jre-6u10-linux-i586.bin from sun's website and after running the binary from terminal as root it has shown some progress and finished installation. Actually it has extracted the content creating a directory (jre1.6.0_10) in the same directory where jre-6u10-linux-i586.bin was. Now the package manager and the system don't recognize it. Surely I can install sun-java packages using apt-get or synaptic. But I want to know if there is a way to make the manual installation working. Should I copy the installation directory to somewhere else?

---

### Post by taurus on 2008-11-21
> **afzal_du said:**
> I've also downloaded jre-6u10-linux-i586.bin from sun's website and after running the binary from terminal as root it has shown some progress and finished installation. Actually it has extracted the content creating a directory (jre1.6.0_10) in the same directory where jre-6u10-linux-i586.bin was. Now the package manager and the system don't recognize it. Surely I can install sun-java packages using apt-get or synaptic. But I want to know if there is a way to make the manual installation working. Should I copy the installation directory to somewhere else?

If I were you, I would move jre-6u10-linux-i586.bin to /opt and unpack it there.

```
sudo mv jre-6u10-linux-i586.bin /opt
sudo ./jre-6u10-linux-i586.bin
```
Then, you need to configure your system to use the new java version in /opt/jre1.6.0_10.

```
sudo update-alternatives --config java
java -version
```

---

### Post by afzal_du on 2008-11-22
Thanks for your quick reply. I'll try that on the next boot (now I'm in windows).

---

### Post by afzal_du on 2008-11-28
sudo update-alternatives --config java
says
No alternatives for java

Can you give the commands in detail plz?

---

### Post by taurus on 2008-11-28
> **afzal_du said:**
> sudo update-alternatives --config java
says
No alternatives for java

Can you give the commands in detail plz?

Did you unpack it in /opt?  What's the output of this command from a terminal?

```
ls -la /opt
```

---

### Post by afzal_du on 2008-11-29
Well, I've romoved the .bin file and installed by apt-get. Thanks again!

---

