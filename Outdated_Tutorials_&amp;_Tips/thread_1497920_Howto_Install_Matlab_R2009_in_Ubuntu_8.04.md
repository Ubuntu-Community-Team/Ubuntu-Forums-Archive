---
title: "Howto: Install Matlab R2009 in Ubuntu 8.04"
date: 2010-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by dragos2 on 2010-05-31
How to install Matlab R2009 Student Edition on Ubuntu 8.04 64 bits.
Tested on server edition (should work on the desktop one as well).

1. If its a remote system get the iso and mount it, otherwise just plug the dvd into dvdrom

2. As root
```

# apt-get install ia32-libs

```3. Start the installer in text mode and use the 32 bit switch(this Matlab version is a 32 bit app)
```

# ./install.sh -t -glnx86

```Accept the license with 'a'

4. Enter where you want it installed like:
```

/usr/local/matlab

```And accept the other default settings.

5. After install the installer will try to run the activator script which will fail. This is normal
since the activator fails on 64 bit OS'es.

Press CTRL + C to close the installer.

6.  Follow the steps from here:
[http://www.mathworks.com/support/solutions/data/1-3YZBZ6.html?solution=1-3YZBZ6](http://www.mathworks.com/support/solutions/data/1-3YZBZ6.html?solution=1-3YZBZ6)

On ubuntu this means that you have your serial number obtained when you bough the product and the machine id is the mac address: /sbin/ifconfig and check after HwAddr

Log in to your Mathworks account, create one if you don't already have.

Click on "Activate Software" in the left panel, provide the serial number and machine id and you will get the license file.

Download it and save it under /usr/local/matlab/licenses/license.dat

7. Edit /etc/profile and type this since Matlab uses its own Java version:
```

export MATLAB_JAVA=/usr/local/mathlab/sys/java/jre/glnx86/jre

```Log off and on.
8. You're done, type
```

matlab -glnx

```to start the application.

Please be aware that you have to type the glnx86 option all the times since you are running a 32 bit Matlab on a 64 bit OS. I don't know about Matlab R2010.


References:
[http://ubuntuforums.org/archive/index.php/t-717976.html](http://ubuntuforums.org/archive/index.php/t-717976.html)
[http://www.mathworks.com/support/solutions/data/1-3YZBZ6.html?solution=1-3YZBZ6](http://www.mathworks.com/support/solutions/data/1-3YZBZ6.html?solution=1-3YZBZ6)

---

### Post by contecarli on 2010-08-22
First of all, thank you very much for this thread. I've been trying to install Matlab on my Ubuntu 64bit  server for a long time and never came past the error messages. This is the first time I've seen that you have to install ia32-libs to make it work.

To start the application, there is an easy way to avoid having to add the -glnx86 flag every time you start the application:

Edit /etc/profile and add the following line, creating an alias for the matlab executable:
```
alias matlab='matlab -glnx86'
```
Then there is no longer the need to type '-glnx86' when starting Matlab.

---

