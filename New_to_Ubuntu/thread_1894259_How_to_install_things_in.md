---
title: "How to install things in"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by juxifeng on 2011-12-12
Hello everyone,

I am an absolute beginner of ubuntu. I started to use ubuntu just because my university asked me to do an engineering progect which require using Computational Fluid Dynamics software. They cost a lot if you buy such on in Windows, but in ubuntu there are absolute free ones.

The one I want to download is Openfoam. If any one of you are willing to help, please see the two attached links:
This is the official website of Openfoam: [http://www.openfoam.com/download/ubuntu.php](http://www.openfoam.com/download/ubuntu.php)
This is a guide to install: [http://code-saturne.blogspot.com/2010/01/installation-of-openfoam-16-on-ubuntu.html](http://code-saturne.blogspot.com/2010/01/installation-of-openfoam-16-on-ubuntu.html)

So, I followed what the guide say, and typed into the terminal and entered my password.
```
/$ sudo apt-get install cmake g++ flex++ bison python qt4-designer binutils-dev zlib1g-dev

```
Then I think things are not as expected. The terminal appeared the following lines:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'flex' for regex 'flex+'
Note, selecting 'flex-doc' for regex 'flex+'
Note, selecting 'jflex' for regex 'flex+'
Note, selecting 'flex-old' for regex 'flex+'
Note, selecting 'cl-flexi-streams' for regex 'flex+'
Note, selecting 'cl-flexichain' for regex 'flex+'
Note, selecting 'flex-old-doc' for regex 'flex+'
Note, selecting 'flexbackup' for regex 'flex+'
Note, selecting 'flexloader' for regex 'flex+'
Note, selecting 'flexml' for regex 'flex+'
Note, selecting 'kdmflexiserver' for regex 'flex+'
Note, selecting 'libdatetime-format-flexible-perl' for regex 'flex+'
Note, selecting 'libflexdock-java' for regex 'flex+'
Note, selecting 'libflexdock-jni' for regex 'flex+'
Note, selecting 'libflexdock-java-doc' for regex 'flex+'
Note, selecting 'libflexdock-java-demo' for regex 'flex+'
Note, selecting 'libflexmock-ruby' for regex 'flex+'
Note, selecting 'libflexmock-ruby1.8' for regex 'flex+'
Note, selecting 'libflexmock-ruby1.9.1' for regex 'flex+'
Note, selecting 'flexmem' for regex 'flex+'
Note, selecting 'obexftp' instead of 'flexmem'
E: Unable to locate package zliblg-dev
```

Ok, here are my questions:
1. What does these lines mean:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
2. What is 'Note, selecting'
3. Why didn't the terminal mention 'cmake', 'g++' and the other ones?
4. The last line 'Unable to locate package zliblg-dev', what can I do about that?
5. How can I check if a software is installed correctly?

It would be great if you can answer these beginner questions. But if anyone are kind to offer a help to guide me go through the entire downloading process up until I am able to use Openfoam, I would be really thankful.

Jin

---

### Post by juxifeng on 2011-12-12
:) Please help.

---

### Post by tartalo on 2011-12-12
You tried to install zliblg-dev when the instructions told you to install zlib1g-dev

The letter l and the number 1 are very simmilar, that's why I prefer to copy-paste.

---

### Post by BC59 on 2011-12-12
For you it's better to follow the instructions from here:
[http://www.openfoam.com/download/ubuntu.php](http://www.openfoam.com/download/ubuntu.php)

So first install the Openfoam repository and then follow the instructions to update and install.

---

### Post by juxifeng on 2011-12-12
> **tartalo said:**
> You tried to install zliblg-dev when the instructions told you to install zlib1g-dev

The letter l and the number 1 are very simmilar, that's why I prefer to copy-paste.

Thank you for that spot. This time the code gets better:

cmake is already the newest version.
python is already the newest version.
qt4-designer is already the newest version.
qt4-designer set to manually installed.
zlib1g-dev is already the newest version.
zlib1g-dev set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 flex-old : Conflicts: flex but 2.5.35-10ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

But still, things like 'g++' are not mentioned. And how can I install the things that terminal could not install?

Thank you.

---

### Post by juxifeng on 2011-12-12
> **BC59 said:**
> For you it's better to follow the instructions from here:
[http://www.openfoam.com/download/ubuntu.php](http://www.openfoam.com/download/ubuntu.php)

So first install the Openfoam repository and then follow the instructions to update and install.

Thank you very much for you suggestion.

I followed that instruction by coping and pasting this into terminal:
VERS=`lsb_release -cs`       
sudo sh -c "echo deb [http://www.openfoam.com/download/ubuntu](http://www.openfoam.com/download/ubuntu) $VERS main > /etc/apt/sources.list.d/openfoam.list"

However that's what I have got:
daijin@daijin-VirtualBox:~$ VERS=`lsb_release -cs`
daijin@daijin-VirtualBox:~$ sudo sh -c "echo deb [http://www.openfoam.com/download/ubuntu](http://www.openfoam.com/download/ubuntu) $VERS main > /etc/apt/sources.list.d/openfoam.list"

Not any thing at all happened.
Then I checked my ubuntu version, it is 11.10, which is really a new version, isn't in the list of available version listed in the Openfoam installation page.
Is that the reason why things are not as expected? 
What should I do solve the problem?

Thank you.

---

### Post by BC59 on 2011-12-12
After this you have to continue with the installation, run:

```
sudo apt-get update
```

and then 

```
sudo apt-get install openfoam201
```

---

### Post by juxifeng on 2011-12-12
> **BC59 said:**
> After this you have to continue with the installation, run:

```
sudo apt-get update
```and then 

```
sudo apt-get install openfoam201
```

Thank you for your reply.
I tried this, and this appears:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package openfoam201

Unable to locate package. Is it because I am using the newest version of ubuntu?

Thank you.

---

### Post by grahammechanical on 2011-12-12
Hi

You ask

> Unable to locate package. Is it because I am using the newest version of ubuntu?

I would say the answer is no. Why is the install program unable to locate openfoam201 (the openfoam program) so that it can install it?

1) the program openfoam201 is in the wrong folder.

2) the openfoam201 Ubuntu Deb package has not been downloaded.

I have just gone on to the openfoam web site and I have been unable to download the openfoam Ubuntu Deb package vesion 2.0.1.

Regards.

---

### Post by mlentink on 2011-12-12
> **juxifeng said:**
> Thank you for your reply.
I tried this, and this appears:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package openfoam201

Unable to locate package. Is it because I am using the newest version of ubuntu?

Thank you.


Yes.

In place of the code mentioned under "1" on the Openfoam site, use this one:
```
sudo sh -c "echo deb http://www.openfoam.com/download/ubuntu natty main > /etc/apt/sources.list.d/openfoam.list"
```Then proceed with the rest of the steps.
The package cannot be found because the Openfoam repository does not yet contain a directory for oneiric (the current version) yet. In all likelihood, the version for natty will work on your system.

---

### Post by juxifeng on 2011-12-12
> **mlentink said:**
> Yes.

In place of the code mentioned under "1" on the Openfoam site, use this one:
```
sudo sh -c "echo deb http://www.openfoam.com/download/ubuntu natty main > /etc/apt/sources.list.d/openfoam.list"
```Then proceed with the rest of the steps.
The package cannot be found because the Openfoam repository does not yet contain a directory for oneiric (the current version) yet. In all likelihood, the version for natty will work on your system.

Thank you for your advice. You made me think, and now I have understand. I tried the code but except this time the terminal asked me to provide the password, it didn't do anything. So, can I already blame it is the version which stopped me?

If this is the case, what can I do to solve the problem? Certainly not to wait until the new release...
Thanks
Jin

---

### Post by juxifeng on 2011-12-12
> **grahammechanical said:**
> Hi

You ask



I would say the answer is no. Why is the install program unable to locate openfoam201 (the openfoam program) so that it can install it?

1) the program openfoam201 is in the wrong folder.

2) the openfoam201 Ubuntu Deb package has not been downloaded.

I have just gone on to the openfoam web site and I have been unable to download the openfoam Ubuntu Deb package vesion 2.0.1.

Regards.

Thank you for the answer.
When you said openfoam201 is in the wrong folder, do you mean it is the official website who didn't arrange well? Because in my computer there still isn't a folder for Openfoam yet.
Regards,
Jin

---

### Post by BC59 on 2011-12-12
Maybe it did something and the Openfoam repository is included in your sources.list

Check now if you can install it.

sudo apt-get update
sudo apt-get install openfoam201

---

### Post by juxifeng on 2011-12-12
> **BC59 said:**
> Maybe it did something and the Openfoam repository is included in your sources.list

Check now if you can install it.

sudo apt-get update
sudo apt-get install openfoam201

Thank you for the answer.
Wow, it worked after I have updated. Can you explain briefly what sources.list is, because now these are all magical for me.

The terminal did lots of getting, unpacking, setting up, and finally it comes to these few lines:
Code:
Setting up openfoam201 (0-1) ...

** To use OpenFOAM please add
**
**    . /opt/openfoam201/etc/bashrc
**
** To your ~/.bashrc

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

I don't understand how actually I add . /opt/openfoam201/etc/bashrc to my  ~/.bashrc in order to open it.
Would you help me on that?

Thank you.
Jin

---

### Post by BC59 on 2011-12-12
Next step is to install Paraview:

```
sudo apt-get install paraviewopenfoam3101 
```

after that run to open the file bashrc:

```
gedit ~/.bashrc
```

At the bottom of that file, add the following line and save:

> source /opt/openfoam201/etc/bashrc

Then to use the program you have to follow the instructions:

Getting Started

Create a project directory within the $HOME/OpenFOAM directory named <USER>-2.0.1 (e.g. chris-2.0.1 for user chris and OpenFOAM version 2.0.1) and create a directory named run within it, e.g. by typing:

```
mkdir -p $FOAM_RUN
```

Copy the tutorial examples directory in the OpenFOAM distribution to the run directory. If the OpenFOAM environment variables are set correctly, then the following command will be correct:

```
cp -r $FOAM_TUTORIALS $FOAM_RUN 
```

Run the first example case of incompressible laminar flow in a cavity:
```
cd $FOAM_RUN/tutorials/incompressible/icoFoam/cavity 
blockMesh 
icoFoam 
paraFoam
```

---

### Post by juxifeng on 2011-12-12
> **BC59 said:**
> Next step is to install Paraview:

```
sudo apt-get install paraviewopenfoam3101 
```after that run to open the file bashrc:

```
gedit ~/.bashrc
```At the bottom of that file, add the following line and save:



Then to use the program you have to follow the instructions:

Getting Started

Create a project directory within the $HOME/OpenFOAM directory named <USER>-2.0.1 (e.g. chris-2.0.1 for user chris and OpenFOAM version 2.0.1) and create a directory named run within it, e.g. by typing:

```
mkdir -p $FOAM_RUN
```Copy the tutorial examples directory in the OpenFOAM distribution to the run directory. If the OpenFOAM environment variables are set correctly, then the following command will be correct:

```
cp -r $FOAM_TUTORIALS $FOAM_RUN 
```Run the first example case of incompressible laminar flow in a cavity:
```
cd $FOAM_RUN/tutorials/incompressible/icoFoam/cavity 
blockMesh 
icoFoam 
paraFoam
```

It worked, finally.
Many thanks for your help!
: )

---

