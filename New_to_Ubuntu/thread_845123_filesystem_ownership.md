---
title: "filesystem ownership"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by coldfire80 on 2008-06-30
Hello everyone... 

i've successfully installed ubuntu in my system... its version is 6.06 and i was having a problem with it's filesystem... when i go to 

computer-->filesystem-->properties-->permissions

file owner says "unknown"... im also trying to run an XAMPP server in it but when i try to access a page in localhost, it states an error 

"permission denied in unknown".. 

so i guess this owner thing might be the problem... 

now the question.. 

how can i change the file system's owner to user "coldfire" (my username)?

thanks for anyone who read this and any help would be greatly appreciated :)

---

### Post by PriceChild on 2008-06-30
I think its best you start off with Ubuntu 8.04 LTS (The Hardy Heron) which is the new stable release of Ubuntu. Dapper is a couple of years old now, and although it works, it will cause compatibility issues with newer apps.

Next, Ubuntu doesn't work like windows. Users only own /home/username, and the 'root' account owns /

You need to use sudo or gksudo to elevate your rights to root. You can read more about root at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by coldfire80 on 2008-06-30
thanks for the response

that sudo was great help... :)

but i still get that "unknown" file owner from...

computer-->filesystem-->properties-->permission

i've tried logging in as root by using *su* and changed some permissions in 

/dev/hda1/

to "coldfire" but yeah, file owner of filesystem in computer was still unknown... is there some way it can be changed to a user or root instead?

thanks again :)

btw, the reason for the old version of ubuntu was because of thesis, by the time im done with it, im switching to the newer one XD

---

### Post by chrisccoulson on 2008-06-30
Why are you trying to do that? If you try playing with permissions and ownership in areas of the filesystem that you don't understand (especially in /dev), you will break your system fairly quickly. It's happened to plenty of other people on here.

By default, the root filesystem ('/') belongs to the root user, and no other user can modify or create files or folders within it. If you need to modify or create a file or folder within the root filesystem, then user sudo - but you shouldn't need to be doing this anyway.

If you explain what you are trying to achieve, someone here will be able to help

---

