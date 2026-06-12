---
title: "Cant Open Firefox!"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Ashfaqur Rahman on 2013-04-05
I cant open firefox from my desktop icon.
When I click on the desktop icon it says " Your firefox icon cannot be loaded.It may be missing or inaccessible ".
How I can solve this problem?

I am using Ubuntu 12.10 Desktop.

---

### Post by fantab on 2013-04-05
Try From Terminal:
```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by Ashfaqur Rahman on 2013-04-06
I Have Tried This But It Doesnt Work! :(

---

### Post by moody_mark on 2013-04-06
usually firefox points to /usr/bin/firefox

try opening a terminal and typing

```
which firefox
```

You should see something like

```
/usr/bin/firefox
```

---

### Post by Ashfaqur Rahman on 2013-04-06
Yes I Have Seen This But It Didn't Solve The Problem. @moody_mark

One More Thing If I Open Firefox With This Code:
```
sudo firefox
```
It shows following notes in terminal
** (firefox:5096): WARNING **: Failed to open webapp application path dir /usr/local/share/unity-webapps/userscripts: Error opening directory '/usr/local/share/unity-webapps/userscripts': No such file or directory

---

### Post by Impavidus on 2013-04-06
1: Firefox, being a graphical application, can better be opened with **gksudo firefox** than with **sudo firefox**. Don't use the latter.
2: More importantly, most security threats enter your system via the web browser. Therefore, never run firefox with root privileges, so never use **gksudo firefox** either.
3: If you type```
firefox
``` in your terminal, does it indeed start firefox, possibly with a warning, or does it not start (or maybe start and immediately exit)? In the first case there is an error in your launcher, in the second case the error is in firefox itself.
4: Does firefox work from the guest account?

---

### Post by Ashfaqur Rahman on 2013-04-07
If I tried open with this code:
```

firefox

```

It gives error: access denied cant load your firefox profile

Yes Can open firefox from guest account!!!!

---

### Post by fantab on 2013-04-07
Try deleting the **.mozilla** folder after pressing Ctrl+H in the File Browser. Then start firefox. [You will lose all your firefox customizations once you delete **.**mozilla. there is a dot before the folder name, it keeps the folder/file hidden until you reveal it.]

---

### Post by Impavidus on 2013-04-07
> **Ashfaqur Rahman said:**
> If I tried open with this code:
```

firefox

```

It gives error: access denied cant load your firefox profile

This may be because you tried opening firefox with **sudo firefox**. Your .mozilla directory or a subdirectory may be owned by root. That's the reason for point #1 in my previous post. You'll need to run nautilus with root privileges to delete the it, but instead you can try setting the owner back to yourself, so that you don't lose your bookmarks.

---

### Post by Ashfaqur Rahman on 2013-04-07
What is file browser? I cant understand! @fantab

What is nautilus? How can I run it? @impavidus

---

### Post by Impavidus on 2013-04-07
Nautilus is your file browser, also known as file manager. If you're indeed using the default Ubuntu you can start it from the dash. To use nautilus with root permissions, open a terminal (use the dash) and type```
gksudo nautilus
```Hit enter, give your password and you'll get your file manager that will allow you to change any root-owned files in your home directory (and any other directory). Close the file manager as soon as you are done, to drop your elevated and dangerous permissions.

Instead you can also use the terminal to do everything, but that's something we don't recommend to beginners.

---

### Post by Ashfaqur Rahman on 2013-04-08
If I open home folder and press Ctrl + H i can see .mozilla folder but when i try to delete it it says " .mozilla cannot be handled because you dont have permisson to read it  ".

If I open home folder with Terminal using
```

sudo nautilus

```

I can see only Desktop in home and after pressing Ctrl + H i cant find .mozilla folder.

What can i do?

---

### Post by fantab on 2013-04-08
Do NOT use "sudo". Just

```
nautilus
```

or just open your file-manager, Nautilus from the launcher... Do you see a folder icon in the launcher?

---

### Post by Impavidus on 2013-04-08
> **Ashfaqur Rahman said:**
> If I open home folder and press Ctrl + H i can see .mozilla folder but when i try to delete it it says " .mozilla cannot be handled because you dont have permisson to read it  ".
That's because it's owned by root (I think)
> 
If I open home folder with Terminal using
```

sudo nautilus

```

I can see only Desktop in home and after pressing Ctrl + H i cant find .mozilla folder.
That's because you were viewing root's home directory.
> 
What can i do?
Let's try and solve this via the terminal. It makes it easier to give exact instructions.

Open a terminal and give these commands. Pay attention to the l (=ell) and | (=pipe) and to the ~ (=tilde) and - (=hyphen). Copy-paste if you manage to get this page on the affected computer.```

cd ~
ls -al | mozilla
```
In my case it gives something like```

drwx------  4 username username     4096 feb  7 10:20 .mozilla
```
If you get instead something like```

drwx------  4 root root     4096 feb  7 10:20 .mozilla
```
your mozilla directory is indeed owned by root (which is what I suspect). In that case run the command
```

sudo chown -R yourusername:yourusername .mozilla
```of course substituting your user name. When you've done that you should be able again to run firefox from the command line. Then we can get back to your original problem. If firefox still doesn't load, try renaming the **.mozilla** directory to someting like **.mozilla-old**. You will be able to do so without using **sudo** or **gksudo**.

And finally, it's better to use **gksudo nautilus** than **sudo nautilus**. That last command sometimes gives problems, which, in addition to your existing problems, will be even more confusing. See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) for the reason why.

---

### Post by pfeiffep on 2013-04-08
Nautilus is a 'file browser' analagous to windows explorer. It should be launched by clicking on it's icon, but if you don't know what the icon looks like you can launch it from a terminal

to access a terminal window use these keys at the same time

```
Ctrl-Alt-t
```

Once in the terminal type
```
nautilus
```

This will launch the file browser

If you need to delete files from within nautilus and you receive a message that you don't have permission you should launch it with these commands
```
gksudo nautilus
```

[COLOR=#ff0000]**Be careful **[/COLOR]with this since it enables you to delete just about anything

---

### Post by Ashfaqur Rahman on 2013-04-08
Yahoo! That worked!! Thanks Impavidus,
But can you plz explain what we have done actually with this code?
```

sudo chown -R uname:uname .mozilla

```

---

### Post by Impavidus on 2013-04-08
Your .mozilla directory was owned by root. With that command you changed ownership back to yourself, so now firefox regained the right to edit files in the .mozilla directory when running it as normal user. That's what it needs to run.

And what about the lancher on the left side of your screen, does it work again?

---

### Post by Ashfaqur Rahman on 2013-04-08
Yes Its working again!

---

### Post by Impavidus on 2013-04-08
Great! Glad I could help.

The normal "mark as solved" functionality is broken at the moment, but you can go to your first post, click "edit", click "go advanced" and change the prefix to "solved". This will tell other people you solved your problem, so they can spend their time solving other people's problems.

---

### Post by Ashfaqur Rahman on 2013-04-08
Yes, if problem solved i always change prefix.
And thanks again for help :)

---

