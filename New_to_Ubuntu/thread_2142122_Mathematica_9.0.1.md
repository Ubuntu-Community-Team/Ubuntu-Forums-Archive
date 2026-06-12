---
title: "Mathematica 9.0.1"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by Asadik on 2013-05-04
I am trying to install Mathematica 9.0.1 on my Ubuntu as it continued to crash on my windows partition and my University labs seem to use linux for that program. I am having troubles installing this, however. I googled many steps and took them but I keep getting this error:

Error: Cannot create directory /usr/local/Wolfram/Mathematica/9.0.


You may need to be logged in as root to continue with this installation.


Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/Mathematica/9.0:


I did create a root account by following a tutorial and that still didn't work it just closes with an error. I also attempted to use Synaptic Package Manager, but the Mathematica .sh file is greyed out and I can't select it.

Please help me as I need this program,

thank you in advance.

---

### Post by codingman on 2013-05-04
You need to open up a terminal, and type in:
```
sudo nautilus
```
It will ask for the root password, so type it in. It does not show your password onscreen, so just type in the password and then hit ENTER. It should bring up the file manager. Run the mathematica script, and continue with the installation. It should work.

---

### Post by Asadik on 2013-05-04
Hi,

I tried this, it didn't ask for the root password. And also did the verifying and gave an error message and closed too quickly for me to read the message.

---

### Post by codingman on 2013-05-04
Try "sudo su". If it does not ask for password, then there is an issue or you are not logged into the root account.

---

### Post by Asadik on 2013-05-04
I will try this quick. But it does say root@ my account name is that what it should say if I'm in a root account?

---

### Post by Asadik on 2013-05-04
yes I must be in the wrong one because it didn't ask for a password again

---

### Post by Impavidus on 2013-05-04
Please, disable your root account again. You won't need it for installation of mathematica and it's too risky (unless you really know what you are doing, which you don't. Sorry.). See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for the proper instructions.

The way to install this is using sudo:```
sudo ./install_script
```substituting the name of the install script. Enter your own password, not the root password. This will convince the installer you're root and run it with root permissions.

---

### Post by monkeybrain2012 on 2013-05-04
You can use sudo to run the install script as in post #7, or, you can install Mathematica in your Home directory which doesn't require sudo. Mathematica's install script asks you where would you want it to be installed, /usr/local/Wolfram is the default, but you can override that.

---

### Post by codingman on 2013-05-04
Then you are root. If you want it to be in your filesystem, then you need to be root, if you want it to be in your /home directory, then you do not need to be root. If you want it to be in your home directory, then you need to suggest the install path to be /home/*your_username*/Mathematica , with your_username being, well, your username. You can set the last folder to be as you like.

---

### Post by wsxadf on 2013-05-05
I agree with [**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721"). Using a root account when user is not familiar with linux machine is not a good idea. Use sudo or install mathematica in home directory (that's what i did). Try read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo). It will help understanding what sudo does.

---

### Post by codingman on 2013-05-05
Sudo contains much power, but if you are told what to do with it, it is not so bad. However, you may install it in your home directory, this will keep Root and the *sudo* command out of the way.

---

### Post by rewyllys on 2013-05-05
Asadik, take a look at the thread at this URL:  [http://ubuntuforums.org/showthread.php?t=2094436](http://ubuntuforums.org/showthread.php?t=2094436)

And, the advice you've received from others to use "sudo", rather than logging in as root, is quite correct.

---

