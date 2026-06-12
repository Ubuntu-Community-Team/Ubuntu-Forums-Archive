---
title: "why doesn't these guides work for me?"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by nemespheric on 2012-05-18
apologies for repost, i had to use a different id, because of my  aspergers  and obsessive compusive disorderliness

okay so i have  been trying to accomlish two idfferent things as a complete newbie to  linux, firstly to move the lauchbar down to the bottom as i would like  it there, secondly to enable the system wide pulseaudio eq, i have  followed all of the step listed in these guides:

[http://www.webupd8.org/2011/10/how-t...bottom-of.html]("http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html")

this one said for ubuntu 11.10, but i i installed 12.04 so i am not sure  whether this should work or not, but it did not, it also seems to  mention something about compiz, but i doin't have that, i'm not sure  whether i need it?

[http://ubuntublog.org/move-unity-bar...-in-ubuntu.htm]("http://ubuntublog.org/move-unity-bar-to-bottom-of-screen-in-ubuntu.htm")

this guide does not say anythging about 11.10 and has 12.04 in the tags

[http://ubuntublog.org/move-unity-bar...-in-ubuntu.htm]("http://ubuntublog.org/move-unity-bar-to-bottom-of-screen-in-ubuntu.htm")

it doesn't seem to work either for some reason, it says something about  unity 3d though, i absolutely have no clue which unity i am suing,  seriously whee is that indicvated, i can't even find anything about  unity 3d i've tried standard google searches of unity 3d and and unity  3d wiki and nada, what is unity 3d? what is unity 2d? what are the  differences? i am a little bit disappoint rigsht now, i am going to  foget the eq for now, but seriously why cna't i fix this problem?

i am using ubuntu 12.04 32bit

---

### Post by Frogs Hair on 2012-05-18
The bottom launcher is experimental and I haven't used it . The equalizer can be installed with the following PPA from the terminal. ```
sudo add-apt-repository ppa:nilarimogard/webupd8
``````
sudo apt-get update
``````
sudo apt-get install pulseaudio-equalizer
``` Open the equalizer from dash and use the settings on the right to enable it. I have installed the equalizer with this PPA . There is a .deb package available also and can be opened with the software center.

Unity 3D shows up as Ubuntu in the login screen and you may need a proprietary graphics driver to use it . The CCSM must be installed for the bottom launcher plug-in .

---

### Post by nemespheric on 2012-05-18
okay, could anyone please tell me how to enable unity 3d? thank yoos

---

### Post by Frogs Hair on 2012-05-18
1. Login to Ubuntu 
2. Open additional drivers and install the recommended proprietary graphics driver if available .
3. Install the CompizConfig Settings Manager.

If you have done this choosing Ubuntu from the log-in screen is all that is required.

---

### Post by cariboo on 2012-05-18
> **nemespheric said:**
> okay, could anyone please tell me how to enable unity 3d? thank yoos

It should be enabled by default, which session do you choose when you log into your account?

---

### Post by nemespheric on 2012-05-18
> **cariboo907 said:**
> It should be enabled by default, which session do you choose when you log into your account?

hello, well vasiclaly, i just click my name, then i put my password in which is a and then it just logs in and that's all i have to do, um i tried to get the above guide to work for enabling the lauchbar on the bottom of the screen, but i don't know why it isn't working, here is what the terminal says when i tried:
> 
miles@miles-System-Product-Name:~$ mkdir -p ~/.compiz-1/plugins
miles@miles-System-Product-Name:~$ cd ~/unityshell
miles@miles-System-Product-Name:~/unityshell$ cp libunityshell.so ~/.compiz-1/plugins/
miles@miles-System-Product-Name:~/unityshell$ mkdir /tmp/unityshell
mkdir: cannot create directory `/tmp/unityshell': File exists
miles@miles-System-Product-Name:~/unityshell$ cp *.png /tmp/unityshell/
cp: cannot create regular file `/tmp/unityshell/launcher_arrow_btt.png': Permission denied
cp: cannot create regular file `/tmp/unityshell/launcher_arrow_outline_btt.png': Permission denied
cp: cannot create regular file `/tmp/unityshell/launcher_arrow_outline_ttb.png': Permission denied
cp: cannot create regular file `/tmp/unityshell/launcher_arrow_ttb.png': Permission denied
cp: cannot create regular file `/tmp/unityshell/launcher_pip_btt.png': Permission denied
cp: cannot create regular file `/tmp/unityshell/launcher_pip_ttb.png': Permission denied
miles@miles-System-Product-Name:~/unityshell$ cd /tmp/unityshell/
miles@miles-System-Product-Name:/tmp/unityshell$ chmod 644 *.png
chmod: changing permissions of `launcher_arrow_btt.png': Operation not permitted
chmod: changing permissions of `launcher_arrow_outline_btt.png': Operation not permitted
chmod: changing permissions of `launcher_arrow_outline_ttb.png': Operation not permitted
chmod: changing permissions of `launcher_arrow_ttb.png': Operation not permitted
chmod: changing permissions of `launcher_pip_btt.png': Operation not permitted
chmod: changing permissions of `launcher_pip_ttb.png': Operation not permitted
miles@miles-System-Product-Name:/tmp/unityshell$ sudo chown root:root *.png
[sudo] password for miles: 
a
Sorry, try again.
[sudo] password for miles: 
miles@miles-System-Product-Name:/tmp/unityshell$ 

---

