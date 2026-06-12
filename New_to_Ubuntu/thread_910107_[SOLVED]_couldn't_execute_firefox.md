---
title: "[SOLVED] couldn't execute firefox"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by ellalan on 2008-09-04
Hi
I have been trying to change the firefox icons and I have messed up something. When I try to start firefox I get an error message(see the attachment).
I am able to start from the Terminal and tried reinstallation in Synaptics.
Could someone help me please. TIA.

---

### Post by porchrat on 2008-09-04
do this in terminal:

```
sudo chown YOUR_USERNAME:YOUR_USERNAME /usr/share/pixmaps/firefox3.0.png
```

where YOUR_USERNAME is your actual username

Also do this:

```
sudo chmod 777 /usr/share/pixmaps/firefox3.0.png
```

then you ushouldn't have a problem

---

### Post by aloshbennett on 2008-09-04
Its working from terminal because, the problem is with the icon and firefox as such is working fine.

Can you see whether you have read access on it?
> ls -l /usr/share/pixmaps/firefox-3.0.png

If there is no access, try
> sudo chmod a+r /usr/share/pixmaps/firefox-3.0.png

---

### Post by ellalan on 2008-09-04
Hi porchrat
When I tried your commands I get this:
vignes@vignes-desktop:~$ sudo chown vignes:vignes /usr/share/pixmaps/firefox-3.0.png
vignes@vignes-desktop:~$ sudo chmod 777 /share/pixmaps/firefox-3.0.png
chmod: cannot access `/share/pixmaps/firefox-3.0.png': No such file or directory
vignes@vignes-desktop:~$ 

I have changed firefox3.0 to firefox-3.0 from your code because when I copied and pasted your code I get "No such file or directory" message.

---

### Post by nothingspecial on 2008-09-04
Have a look in /usr/share/pixmaps to see what the icon is called, mines just called firefox.png.

---

### Post by porchrat on 2008-09-04
> **ellalan said:**
> Hi porchrat
When I tried your commands I get this:
vignes@vignes-desktop:~$ sudo chown vignes:vignes /usr/share/pixmaps/firefox-3.0.png
vignes@vignes-desktop:~$ sudo chmod 777 /share/pixmaps/firefox-3.0.png
chmod: cannot access `/share/pixmaps/firefox-3.0.png': No such file or directory
vignes@vignes-desktop:~$ 

I have changed firefox3.0 to firefox-3.0 from your code because when I copied and pasted your code I get "No such file or directory" message.

post the output of this please:

```
ls -l /usr/share/pixmaps/
```

---

### Post by ellalan on 2008-09-04
Hi nothingspecial
"firefox-3.0.png" is in /usr/share/pixmaps.

---

### Post by porchrat on 2008-09-04
yes but what are its permissions?

Who is the owner?

and what group does it belong to?

---

### Post by nothingspecial on 2008-09-04
My /usr/share/pixmaps/firefox.png  is just a link to /usr/share/firefox/icons/mozicon50.png

That maybe the icon you need to change the permissions for.
First check your /usr/share/firefox/icons directory as to what the file name of the icon is

(I`m still on FF2 so I can`t check)

Then repeat the commands to change permissions from earlier in this thread but use that path instead.

```
sudo chmod 777 /usr/share/firefox/icons/what_its_called.png
```

---

### Post by porchrat on 2008-09-04
nicely done nothingspecial...thats probably it...stupid symbolic links

---

### Post by ellalan on 2008-09-04
Hi nothingspecial
I get this:
:~$ sudo chmod 777 /usr/share/firefox/icons/firefox-3.0.png
[sudo] password for vignes: 
chmod: cannot access `/usr/share/firefox/icons/firefox-3.0.png': No such file or directory

---

### Post by nothingspecial on 2008-09-04
Then we really will have to check.
Can you copy and paste what the terminal says when you type this please
```

ls -l /usr/share/pixmaps/
```

---

### Post by ellalan on 2008-09-04
Hi Guys
I have just managed to rectify and am able to access FF3 without any problems.
This is what I did:
Right clicked the Ubuntu logo=> Edit menus
From Internet=> Firefox Web Browser
Clicked on the FF icon and clicked "Revert" and closed.
Thanks a lot to you all for helping me to resolve this, I'll be more cautious when meddling with these hidden folders.

---

### Post by nothingspecial on 2008-09-04
Excellent. Glad you got it sorted,

---

### Post by ellalan on 2008-09-04
a

---

### Post by porchrat on 2008-09-04
Well done and the important thing is that you have gained more knowledge in your pursuit of the solution

---

