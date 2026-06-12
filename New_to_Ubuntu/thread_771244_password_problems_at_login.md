---
title: "password problems at login"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ginestre on 2008-04-27
For some reason I keep getting 'wrong password' to my log in attempts. I've booted up in recovery mode, done a passwd username just so that I'm sure I'm using the right password (I know I am, but I checked anyhow) but am still unable either to login at the incriminated machine or to ssh to that machine from others, with that password. What might have broken?

---

### Post by riven0 on 2008-04-27
Do you have the liveCD? I think if you boot up the cd, mount your hard drive and delete the hashed password in **/etc/shadow** file, then the root password will be set to nothing. Someone may have a better solution, though.

---

### Post by ginestre on 2008-04-28
Thanks for the reply. The problem turned out to be hardware, after all: the keyboard had gone crazy and was no longer sending correct sequences to the o/s, which naturally objected... changing keyboards solved the issue.

---

