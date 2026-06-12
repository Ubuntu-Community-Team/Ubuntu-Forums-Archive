---
title: "Want to use firefox as web browser."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by PHATSPEED7x on 2008-06-29
I decided to go with kubuntu (I like it's shine). I've downloaded firefox 3, but how do I get it to install? I open the install link, and all it wants to do is extract files.:confused:

---

### Post by jamesrfla on 2008-06-29
You do have to extract the files in order for Firefox to install.

---

### Post by sports fan Matt on 2008-06-29
I thought FF3 was installed in Kubuntu by default (just like in ubuntu)

---

### Post by jamesrfla on 2008-06-29
I though it was too.

---

### Post by Kalinda on 2008-06-30
Nope, it's not, Konqueror is Kubuntu's default browser.

However, if you extract the Firefox tarball into your home folder and open up the console and then type '/firefox/firefox', you should get a handy error telling you to install glib3 I believe. Once you've done that (you'll find it in Adept/Synaptic), you can run Firefox via the shell script called "firefox" which was in the tarball.

Anyhow, you will want to add a link to the Kmenu (right click on the menu and go to "Edit Menu") for it and make sure the command is /home/username/firefox/firefox. If you want to give it an icon, you'll find them in the icons folder in your firefox folder. After that you can put the shortcut/link on yer desktop or panel or whatever.

I actually think it's better because it runs updates directly from Mozilla and it's easy to install plugins like Flash because you just toss the .so files into your plugins subfolder.

---

### Post by cariboo on 2008-06-30
You can install firefox3 from the repositories, no need to go through all the hassle of manually installing it. There are three ways to do this. Add/Remove Programs, Synatic Package Manager or from a command line.

```
sudo apt-get install firefox
```

Jim

---

### Post by kansasnoob on 2008-06-30
Just go to synaptic and search for and select 

> firefox

but first make absolutely sure that your software sources are correct!

In the gnome desktop they'll look like this:

[ATTACH]75844[/ATTACH]

[ATTACH]75845[/ATTACH]

[ATTACH]75846[/ATTACH]

---

### Post by kansasnoob on 2008-06-30
Oops bad screenshot:

[ATTACH]75849[/ATTACH]

---

### Post by stchman on 2008-06-30
> **PHATSPEED7x said:**
> I decided to go with kubuntu (I like it's shine). I've downloaded firefox 3, but how do I get it to install? I open the install link, and all it wants to do is extract files.:confused:

Firefox 3 is not installed by default in Kubuntu.  To get FF3 do this in a terminal.

```
sudo apt-get install firefox-3.0
```

---

### Post by The Cog on 2008-06-30
There is no synaptic in kubuntu. There is adept instead.

You can install firefox using adept, or you can just unpack the download you got. It unpacks into a directory called firefox which contains the program. You can leave it there, or I prefer to copy the unpacked firefox directory to /opt and then link the executable from /usr/local/bin like this:
```
sudo cp -r firefox /opt/firefox
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
```
I'm a bit paranoid about using the ubuntu firefox since I discovered the ubuntu devs modify the javascript interpreter. Some of our company web pages were literally unrecognisable in the ubuntu firefox but looked perfectly normal in the exact "same" build directly from mozilla.

---

### Post by stchman on 2008-06-30
> **The Cog said:**
> There is no synaptic in kubuntu. There is adept instead.

You can install firefox using adept, or you can just unpack the download you got. It unpacks into a directory called firefox which contains the program. You can leave it there, or I prefer to copy the unpacked firefox directory to /opt and then link the executable from /usr/local/bin like this:
```
sudo cp -r firefox /opt/firefox
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
```
I'm a bit paranoid about using the ubuntu firefox since I discovered the ubuntu devs modify the javascript interpreter. Some of our company web pages were literally unrecognisable in the ubuntu firefox but looked perfectly normal in the exact "same" build directly from mozilla.

I do not use synaptic that much.  I prefer the apt-get command line.

---

