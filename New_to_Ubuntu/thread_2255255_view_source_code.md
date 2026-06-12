---
title: "view source code"
date: 2014-12-03
forum: New to Ubuntu
---

### Post by Paul_Armstrong on 2014-12-03
hi Guys can any one tell me how i can view source code for pro grammes such as Aisleriot Solitaire, i am not going to change anything just intrested in seeing the source code.

Thanks in advance 
Paul

---

### Post by slickymaster on 2014-12-03
[https://git.gnome.org/browse/aisleriot/](https://git.gnome.org/browse/aisleriot/)

---

### Post by Paul_Armstrong on 2014-12-03
How and can you view it within linux rather than via the web? the reason for this is just out of interest and i am trying to learn to use linux

---

### Post by deadflowr on 2014-12-03
```
apt-get source <packagename>
```
If you've enable the source repositories, you run the above command and the source package for whichever package you want will download into which directory you are currently in.
No need for sudo, since it's not installing anything.
Typically you would make a new directory/folder somewhere, maybe in Downloads, move into said directory and run the apt-get command.
Then you can dig through the code to your hearts content.

---

### Post by Paul_Armstrong on 2014-12-03
i have typed this command into terminal and got the following message on terminal any help as i say i am brand new 

paul@paul-HP-620:~$ apt-get source aisleriot solitaire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'aisleriot' packaging is maintained in the 'Svn' version control system at:
svn://anonscm.debian.org/pkg-gnome/desktop/unstable/aisleriot
E: Unable to find a source package for solitaire
paul@paul-HP-620:~$

---

### Post by slickymaster on 2014-12-03
You can either clone a copy of the repository of the source code from Git or just branch a particular project.

Have a read at [https://wiki.gnome.org/Git/Developers](https://wiki.gnome.org/Git/Developers)

---

### Post by deadflowr on 2014-12-03
> **Paul_Armstrong said:**
> i have typed this command into terminal and got the following message on terminal any help as i say i am brand new 

paul@paul-HP-620:~$ apt-get source aisleriot solitaire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'aisleriot' packaging is maintained in the 'Svn' version control system at:
svn://anonscm.debian.org/pkg-gnome/desktop/unstable/aisleriot
E: Unable to find a source package for solitaire
paul@paul-HP-620:~$
 apt-get reads that as two different packages.
aisleriot and solitaire, not aisleriot solitaire.
The package though is simply aisleriot.
It's erroring out because there is no package called solitaire.
Package names are one long unbroken string.
A break makes the system think another packages is also wanted.
It's a basic function of apt that allows you to download and install a slew of packages at once.
If that make sense.

---

### Post by Paul_Armstrong on 2014-12-03
sorry again it is now saying check that "DPKG-DEV" package is installed child process failed

---

### Post by deadflowr on 2014-12-03
```
sudo apt-get install build-essential 
```
dpkg-dev is needed to actually work with the source packages.
it should come in with the build-essential package.

---

### Post by Paul_Armstrong on 2014-12-03
massive help that Deadflowr not sure if this has worked or what ave done or were it has gone so hopefully this will be the last question.
Has it worked?
and were is it?
again i am brand new to this so really sorry if this is simple stuff 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'aisleriot' packaging is maintained in the 'Svn' version control system at:
svn://anonscm.debian.org/pkg-gnome/desktop/unstable/aisleriot
Skipping already downloaded file 'aisleriot_3.10.2-1.dsc'
Skipping already downloaded file 'aisleriot_3.10.2.orig.tar.xz'
Skipping already downloaded file 'aisleriot_3.10.2-1.debian.tar.xz'
Need to get 0 B of source archives.
gpgv: Signature made Sat 01 Mar 2014 14:46:48 GMT using DSA key ID 4A08B2FE
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./aisleriot_3.10.2-1.dsc
dpkg-source: info: extracting aisleriot in aisleriot-3.10.2
dpkg-source: info: unpacking aisleriot_3.10.2.orig.tar.xz
dpkg-source: info: unpacking aisleriot_3.10.2-1.debian.tar.xz
dpkg-source: info: applying 02_desktop-path.patch
paul@paul-HP-620:~$

---

### Post by deadflowr on 2014-12-03
Run 
```
ls
```
is there now a folder called aisleriot_3.10.2
Alternately, you can open Files(the gui program) and look to see if a new folder is showing for it.
If so, then simply open the folder and the source contents should be in there.

---

### Post by Paul_Armstrong on 2014-12-03
thats great that thanks for your help can i do that now to view any source code?

---

### Post by deadflowr on 2014-12-03
> **Paul_Armstrong said:**
> thats great that thanks for your help can i do that now to view any source code?
 You can use apt-get source on any source package that is within the Ubuntu repository system.
Otherwise you'd need to download the source package, either using git clone, or wget or via your browsers download  function.
Then you would also need to extract the contents of whichever medium the source code is contained in, most likely a tarball.
Any source package you get that comes in a tar file you would need to extract yourself, though.
You might have noticed that the apt-get source command extracted it automatically for you.
Simple enough though, Ubuntu has a builtin extraction program, file-roller, also known as Archive Manager.
Double clicking on the tar file should auto-start Archive Manager.

---

### Post by mc4man on 2014-12-03
You're probably gonna to want to take the advice in post 4 about 1st. creating a folder to hold each specific source you are aquring thru apt-get 
Create the folder, cd to it in a terminal, then run your apt-get command.
Much tidier than having these files spread about your home folder

---

### Post by andrew.46 on 2014-12-03
Perhaps an easier way would be the more 'manual' method that deadflowr has mentioned, something like the following:

```

cd $HOME/Desktop && \
mkdir aisleriot_source && cd aisleriot_source && \
wget https://download.gnome.org/sources/aisleriot/3.14/aisleriot-3.14.2.tar.xz && \
tar xJvf aisleriot-3.14.2.tar.xz

```

And yes, this would have to be modified for each particular tarball....

---

