---
title: "new member with many questions in mind"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by nabilsunnah on 2008-04-22
hi there
I am a new user . i have been trying and thinking to install ubunto and  at last i did ; I have many questions if u could plz help me as an open source community : 
1- i want to make a network with a laptop and desktop .the desktop is windows and the laptop is ubunto and  I want to share folders btwn the two
2- i want to share internet connection btwn the two
3- I really want to be an expert in linux and get rid of windows coz I am fed up with it 

there other questions .....

and thanks a lot in advance

---

### Post by Wazoot on 2008-04-22
Well as for the folder sharing Idk if you could share folders between the two. Do you mean 2 computers, one with Windows and one with Ubuntu?

---

### Post by Daveski on 2008-04-22
> **nabilsunnah said:**
> hi there
I am a new user .
Welcome

> 1- i want to make a network with a laptop and desktop .the desktop is windows and the laptop is ubunto and  I want to share folders btwn the two

You can access Windows shares via Ubuntu 'out-of-the-box' simply by browsing the network. This is because Ubuntu has the Samba client which is a client implementation of the Windows *File and Printer Sharing* protocol. This is Ubuntu accessing shares on Windows.

OR you can install Samba daemon (Server) and allow your Ubuntu machine to share folders which Windows machines can connect to. This is more complex to setup though. This is Windows accessing 'Windows' shares on Ubuntu.

> 2- i want to share internet connection btwn the two

I would get a Router if you don't already have one, but both Windows or Ubuntu could be set up to 'share' the internet connection to other clients.

> 3- I really want to be an expert in linux and get rid of windows coz I am fed up with it

Good luck. Just use Ubuntu for a while - it might seem a bit tricky at first, but this will pass as you get more used to a different way of doing things.

---

### Post by sam_delta on 2008-04-22
> **Wazoot said:**
> Well as for the folder sharing Idk if you could share folders between the two. Do you mean 2 computers, one with Windows and one with Ubuntu?

file sharing between ubuntu and windows is possible

as mentioned by Daveski it is easier just to browse your network , but if you wish to install Samba server
heres a video on step by step instructions on ubuntu 6.10 using Samba server file sharing as mentioned above
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

although in the video its done with ubuntu 6.10 it should be the same or very similar in Ubuntu 7.10 or 8.04


-sam

---

### Post by st33med on 2008-04-22
> **nabilsunnah said:**
> 
1- i want to make a network with a laptop and desktop .the desktop is windows and the laptop is ubunto and  I want to share folders btwn the two

You need to setup a network using Windows. Once that is setup, you just go to System --> Network Folders (Or something like that, I forget)
> 
2- i want to share internet connection btwn the two


That is beyond my expertise. I think you can get Windows to do it by Sharing an Internet Connection, but in Linux, I have no idea.

> 
3- I really want to be an expert in linux and get rid of windows coz I am fed up with it 

Well, that takes time and practice. You have already installed Linux, and that is your first step to Linux Nirvana :).

---

### Post by nabilsunnah on 2008-04-22
thks alot for your replies 
Iam making a connection btwn the two wiy$th a little bit old way :) a rj 45 FILE

---

### Post by martrn on 2008-04-22
> **nabilsunnah said:**
> hi there
I am a new user . i have been trying and thinking to install ubunto and  at last i did ; I have many questions if u could plz help me as an open source community : 1- i want to make a network with a laptop and desktop .the desktop is windows and the laptop is ubunto and  I want to share folders btwn the two

Hi !

> 2- i want to share internet connection btwn the two
```
sudo apt-get install quagga
```
Ubuntu can be figured to run as a router, linux has the TCP/IP protcol stack built in, as is brillient at it.  Sometimes this involves editing config files to ensure it works properly.  There is no internet connection share wizard...  (Can be a good thing)


> 3- I really want to be an expert in linux and get rid of windows coz I am fed up with it 
Linux it brill.

>  there other questions .....and thanks a lot in advance

---

### Post by nabilsunnah on 2008-04-23
> **martrn said:**
> Hi !


```
sudo apt-get install quagga
```


.

thanks a lot 
 I did the code  ther is a msg asking me to give a password
I tried to type my password but it neither accept numbers nor letters and when I click enter it says sorry try again

---

### Post by jken146 on 2008-04-23
> **nabilsunnah said:**
> thanks a lot 
 I did the code  ther is a msg asking me to give a password
I tried to type my password but it neither accept numbers nor letters and when I click enter it says sorry try again

Just type your password.  You don't see any feedback, but just type it anyway and press Enter.

---

### Post by nabilsunnah on 2008-04-23
I did but the command shell refuses to write

---

### Post by spec-chum on 2008-04-23
You won't see any characters or the cursor moving when you type your password.  That's a security feature.  Just type the password correctly and press Enter.  That'll work.

---

### Post by nabilsunnah on 2008-04-23
thanks a alot 
 I typed the password although it did not appear  and then hit enter ;then  there is a msg saying :
lecture des listes de paquets .... fait 
construction de l'arbre des dépendance
lecture des informations d'état...fait 
E : impossible de trouver le paquet quagga

another problem raised , 
is that I when looking in the network section ubunto can only sse the artitions of windows that are installed in the laptop
 and the network icon show that there is a network connections established with a 100mg but still the internet is not connected and I cant see the desktop partitions in the laptop

---

