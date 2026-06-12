---
title: "editing smb.conf with gedit"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by penasjr on 2012-06-28
I am a first timer on linux..

I installed an ubuntu 12.4 server . on a clone with asus mb and celeron
processor with 1 gig of ram

I included samba as one of my package task.

After installing , I was instructed to edit the smb.conf.

  sudo gedit /etc/samba/smb.conf

But I got an error msg "Bad command"

I tried to install gedit by this command line  ;  sudo apt-get install gedit

I get "unable to locate package gedit"

I thought gedit is normally included in the installation ? 

Good people out there.. pls help !:-$

---

### Post by spikoley on 2012-06-28
The program gedit is a graphical program like notepad in Windows.  Since you installed the server version you do not have a graphical interface.  The solution is to use a terminal text editor like nano or vi.  Both come default with every Ubuntu installation, so there is no need to install anything.

```
sudo nano /etc/samba/smb.conf
```

---

### Post by penasjr on 2012-06-28
> **spikoley said:**
> The program gedit is a graphical program like notepad in Windows.  Since you installed the server version you do not have a graphical interface.  The solution is to use a terminal text editor like nano or vi.  Both come default with every Ubuntu installation, so there is no need to install anything.

```
sudo nano /etc/samba/smb.conf
```

yes  I tried but got this ...

sudo: nano: command not found

there is something wrong somewhere ..

---

### Post by ubudog on 2012-06-28
> **penasjr said:**
> yes  I tried but got this ...

sudo: nano: command not found

there is something wrong somewhere ..

Try: 
```
sudo apt-get install nano
```

---

### Post by penasjr on 2012-06-28
I am getting something after that :

sudo apt-get install nano

so by default nano is not installed

thanks a lot sir ... i think i will be going forward

---

### Post by spikoley on 2012-06-28
> **penasjr said:**
> I am getting something after that :

sudo apt-get install nano

so by default nano is not installed

thanks a lot sir ... i think i will be going forward

My bad.  It has been a while since I set up a server.

Make sure you mark this thread as Solved.  Go to Thread Tools to do so.

---

