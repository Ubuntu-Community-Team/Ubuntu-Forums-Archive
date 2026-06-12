---
title: "Compiling NS3 C++ program environment variables"
date: 2013-04-29
forum: Packaging and Compiling Programs
---

### Post by binaryperson on 2013-04-29
Hello. I installed the NS3 simulator on my computer by following the instructions here:

[HTML]http://yeaptips.blogspot.com/2011/10/ns-3-installation-on-ubuntu-1110.html[/HTML]
[HTML]http://www.brunosilva.info/2012/08/installing-ns-3-on-ubuntu-1204.html[/HTML]

I tried to compile my program but I got this error:

```
$ g++ -Wall -o program1 program1.cpp -DNS3_ASSERT_ENABLE -DNS3_LOG_ENABLE `pkg-config --libs --cflags libns3.16-core-debug libns3.16-network-debug libns3.16-applications-debug libns3.16-internet-debug libns3.16-point-to-point-debug libns3.16-point-to-point-layout-debug libns3.16-csma-debug libns3.16-csma-layout-debug libns3.16-topology-read-debug libns3.16-wifi-debug`
Package libns3.16-core-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-core-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-core-debug' found
Package libns3.16-network-debug was not found in the pkg-config search path.                                               
Perhaps you should add the directory containing `libns3.16-network-debug.pc'                                                     
to the PKG_CONFIG_PATH environment variable                       
No package 'libns3.16-network-debug' found
Package libns3.16-applications-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-applications-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-applications-debug' found
Package libns3.16-internet-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-internet-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-internet-debug' found
Package libns3.16-point-to-point-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-point-to-point-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-point-to-point-debug' found
Package libns3.16-point-to-point-layout-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-point-to-point-layout-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-point-to-point-layout-debug' found
Package libns3.16-csma-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-csma-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-csma-debug' found
Package libns3.16-csma-layout-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-csma-layout-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-csma-layout-debug' found
Package libns3.16-topology-read-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-topology-read-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-topology-read-debug' found
Package libns3.16-wifi-debug was not found in the pkg-config search path.
Perhaps you should add the directory containing `libns3.16-wifi-debug.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libns3.16-wifi-debug' found
program1.cpp:8:29: fatal error: ns3/core-module.h: No such file or directory
compilation terminated.


```

It seems as though I need to set the environment variables for BASH. I am familiar with environment variables in Windows but I have never set any in Linux. Can I get some help please?

While searching I found this script but I'm not sure how to use it or if it will do the right thing.

[HTML]https://github.com/cawka/ns-3-dce/blob/master/utils/setenv.sh[/HTML]

---

### Post by binaryperson on 2013-04-29
I find it remarkable that no one on this forum knows how to set environment variables in Ubuntu.

---

### Post by steeldriver on 2013-04-29
You can set and export an environment variable like

```
export VAR=value
```

HOWEVER in my experience pkg-config errors of the type you are seeing almost always indicate that you are missing the relevant -dev package(s)

BTW, you realize ns3 is available from the repositories, right?

```
$ apt-cache policy ns3
ns3:
  Installed: (none)
  Candidate: 3.13+dfsg-1
  Version table:
     3.13+dfsg-1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
```

---

### Post by binaryperson on 2013-04-29
I did 

```
apt-cache policy ns3
```

and I get the same output.

Does this mean everything was installed correctly?

---

### Post by steeldriver on 2013-04-29
no, it means it's available (there is a candidate) but not installed

---

### Post by binaryperson on 2013-04-29
So, there are two ways two install NS3, the way I did and this way? What do I need to set the environment variables to? How do I find if I'm missing some dev packages?

---

### Post by steeldriver on 2013-04-29
If you install from repositories, then no compiling is required and the issue of pkg-config / compile environment don't even come up

Downside - you get an older version (3.13 versus the 3.16 that you appear to be trying to compile)

Upside - you get a version whose dependencies are consistent with your current system and which will not break when other stuff gets updated

---

### Post by binaryperson on 2013-04-29
Well, since I'm new to all this I would just like to make it work. Must I now uninstall NS3 3.16? Can I just do ```
sudo apt-get install ns3
```

---

### Post by binaryperson on 2013-04-30
Yes, no, maybe? Anyone out there?

---

### Post by steeldriver on 2013-04-30
assuming that's the package you need, then yes

or if you are not comfortable with the command line you can search for and add it from the Software Center

---

### Post by binaryperson on 2013-04-30
What packages do I need to make NS3 work? This like pulling teeth, was the question I posted not clear? Is there anyone out there who can help install NS3 properly?

---

