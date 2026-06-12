---
title: "Ghosting from Windows to Ubuntu 8.10 server"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by maledikt on 2008-11-20
**Good midnight. (00:34 here) :)**

I'm completely new at Linux, 21 years of age and trying my best to learn how to manage a simple http server, and after that I want to proceed at trying to setup a mail server.

I've got decent knowledge about Windows OS-s but all I know how to do in the Linux terminal is how to use apt-get, ls, cd, mkdir and pico. 

:KS_So far I've managed to do the following:_
[I]Install Apache2 via: apt-get install apache2
Make a public_html folder in my home folder
Make an index.html stating Hello World inside /public_html/
Install Samba via: apt-get install samba
Install Sambaclient via: apt-get install sambaclient
I've managed to access a folder on my Windows machine by using:[/I]
smbclient //benni/base
*my Windows PC's name is Benni and I made a folder on the desktop on it named base and shared it*

But here I've stopped as I cannot find a way to copy, transfer or access the files on Benni. (I've made a text file named asdf.txt which I don't know how to copy/open through smbclient)

:KS_My ideal setup would be:_
[I]That I could access my Ubuntu server via my Windows PC so I don't have to use my second screen for it.

That I could set up my web server from my Windows PC, directly to the Ubuntu server without having to switch over to the server physically[/I]

:KS_Reasons:_
I want my server to run 24/7 in another room, not my own, because I can't sleep as well with the sounds of the fans on the computer. I want it to be plugged in, to electricity and the network and just stay there untouched, and make all my http editing in my main computer, which is a Windows XP.

Hoping to see some replies tomorrow afternoon when I've come home from school, I, Maledikt, bid you goodnight. :)

---

### Post by maledikt on 2008-11-20
Also, I'm having problems using "su -" I just get an "Authentication failure" but when I used sudo my username and password work fine. :(

---

