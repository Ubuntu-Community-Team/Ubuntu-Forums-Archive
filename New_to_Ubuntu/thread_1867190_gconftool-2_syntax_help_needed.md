---
title: "gconftool-2 syntax help needed"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-10-22
So I'm trying to make a customized livecd following [these instructions]("https://help.ubuntu.com/community/LiveCDCustomization"). It's been going along all fine, but I've run into a block formed by my lack of terminal knowledge.

I'm using this example code:
```
gconftool-2 --dump /the/settings/branch/you/need > ~/live/your-new-settings.xml
```
and I'm not sure how to change it. I tried this:
```
gconftool-2 --dump ~/.config/xfce4/xfconf/xfce-perchannel-xml> ~/live/your-new-settings.xml
```
but it didn't work.

So how am I supposed to use this code?

My system settings (panels, windows manager settings, etc.) I found located in ~/.config/xfce4/xfconf/xfce-perchannel-xml

---

### Post by matt_symes on 2011-10-22
Hi

You don't use --dump from a location on your hard drive but from a location in the configuration tree. The configuration tree starts at /.

Try 

```
gconftool-2 --dump /
```or one of the sub branches (in the example below apps)

```
gconftool-2 --dump /apps
```Kind regards

---

### Post by DaimyoKirby on 2011-10-22
Ok, that worked, and it outputted a lot of configuration code, but when I tried to add the rest of the original code back on
```

gconftool-2 --dump /apps > ~/livecdtmp/your-new-settings.xml

```
as well as
```

gconftool-2 --dump /apps > ~/live/your-new-settings.xml

```
and I got the same output as before:
```

bash: /home/alden/livecdtmp/your-new-settings.xml: No such file or directory

```

---

### Post by matt_symes on 2011-10-22
Hi

Do you have the folder livecdtmp in your home directory.

What the output of 

```
ls -d ~/live*
```

Post back here.

Kind regards

---

### Post by DaimyoKirby on 2011-10-22
Yeah, I have a livecdtmp folder:
```

alden@LinuxZombie:~$ ls -d ~/live*
[COLOR="Navy"]/home/alden/livecdtmp[/COLOR]

```

---

### Post by matt_symes on 2011-10-22
Hi

That's odd. Check the permissions of your livecdtmp directory.

Here is my quick test.
```

matthew@matthew-Aspire-7540:~$ mkdir livecdtmp
matthew@matthew-Aspire-7540:~$ ls -dl ~/live*
drwxrwxr-x 2 matthew matthew 4096 Oct 22 20:27 /home/matthew/livecdtmp
matthew@matthew-Aspire-7540:~$ gconftool-2 --dump /apps > ~/livecdtmp/your-new-settings.xml
matthew@matthew-Aspire-7540:~$ ls  ~/live*
your-new-settings.xml
matthew@matthew-Aspire-7540:~$ tail -n5 ~/livecdtmp/your-new-settings.xml 
        <int>0</int>
      </value>
    </entry>
  </entrylist>
</gconfentryfile>
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

### Post by DaimyoKirby on 2011-10-22
I don't know how to find it in terminal, but here's a picture from the properties:
[IMG]http://i.imgur.com/1MkRwl.png[/IMG]

---

### Post by matt_symes on 2011-10-22
Hi

Let's see exactly where it's failing.

First let's export these settings to your home directory. I'll assume you will want all the settings.

Open a terminal and *copy and paste from here* into the terminal
```

gconftool-2 --dump /  > ~/your-new-settings.xml
```Then *copy and paste*

```
mv ~/your-new-settings.xml ~/livecdtmp/
```Also post back the results of
[FONT=monospace]
[/FONT]```
ls -dl ~/live*
```Kind regards

---

### Post by DaimyoKirby on 2011-10-22
```

alden@LinuxZombie:~$ gconftool-2 --dump /  > ~/your-new-settings.xml
alden@LinuxZombie:~$ mv ~/your-new-settings.xml ~/livecdtmp/
alden@LinuxZombie:~$ ls -dl ~/live*
drwxrwxr-x 5 alden alden 4096 2011-10-22 16:16 [COLOR="Navy"]/home/alden/livecdtmp[/COLOR]

```

---

### Post by DaimyoKirby on 2011-10-22
Should I now run the original code as before, or not?

---

### Post by DaimyoKirby on 2011-10-22
Can anyone help?

---

### Post by matt_symes on 2011-10-23
Hi

> **DaimyoKirby said:**
> Should I now run the original code as before, or not?

You have done what the original code was trying to do but you have done it in two steps.

Kind regards

---

### Post by DaimyoKirby on 2011-10-23
Ok. Am I supposed to customize it or add anything to it? Because I was looking through it, and it doesn't seem to have info on my panels or settings;

Since we took files from /, does that mean it took all the files in my filesystem, and dropped them into an xml?

---

### Post by matt_symes on 2011-10-23
Hi

> **DaimyoKirby said:**
> Ok. Am I supposed to customize it or add anything to it? Because I was looking through it, and it doesn't seem to have info on my panels or settings;

It's difficult to help you as i have never done what you are doing. 

Do you have a link to what you are trying to do ?

What version of Ubuntu are you using ? I have just noticed in your signature it says xubuntu 11.10. Is this what you are using ?

The XML file will contain gnomes setting.The settings it contains will be dependent on your version of Ubuntu i believe.

> 
Since we took files from /, does that mean it took all the files in my filesystem, and dropped them into an xml?It took the gnome configuration files stored under ~/.gconf and dumped then into a single file (your-new-settings.xml).

These are just the gnome settings and not all the files on your hard drive.

Kind regards

---

### Post by DaimyoKirby on 2011-10-23
I'm (trying) to follow the instructions [here]("https://help.ubuntu.com/community/LiveCDCustomization").

Yes, I am in fact using Xubuntu 11.10.

Part of the problem is that the instructions I'm trying to follow are based on Ubuntu (and Gnome), and I'm using Xubuntu (and Xfce). Also, I'm not very knowledgeable about system and terminal things.

---

### Post by matt_symes on 2011-10-24
Hi

> **DaimyoKirby said:**
> I'm (trying) to follow the instructions [here]("https://help.ubuntu.com/community/LiveCDCustomization").

Yes, I am in fact using Xubuntu 11.10.

Part of the problem is that the instructions I'm trying to follow are based on Ubuntu (and Gnome), and I'm using Xubuntu (and Xfce). Also, I'm not very knowledgeable about system and terminal things.

I'm not sure if it's a terminal issue. I have not really used Xubuntu and i am not sure of the differences.

Other will help you out here hopefully.

Have a free *bump*.

Kind regards

---

### Post by DaimyoKirby on 2011-10-24
Ok, thanks. Hopefully someone else will know what to do.

---

