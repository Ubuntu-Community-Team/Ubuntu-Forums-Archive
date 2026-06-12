---
title: "how do i open \001 in terminal ?"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by tommyleeds on 2012-08-17
some of me usb sticks show up as \001 but when i try to open it in terminal with cd \001 i get no such file or directory
can any body help ?

---

### Post by NikTh on 2012-08-17
Hi , 
plug a usb and give the results of 
```
ls /media/
```usually external devices mounted under /media folder , maybe the right command is 
```
cd /media/001
```Thanks

---

### Post by tommyleeds on 2012-08-17
cheers NikTh
i get this
\001 apt

---

### Post by sisco311 on 2012-08-17
It seams that there is a literal backslash in the directory name. 

A non-quoted  backslash (\) is the escape character.  It preserves the literal value of the next character that follows, with the exception of <newline>.

You have to quote/escape it. Assuming that you are in /media:
```
cd \\001
```
```
cd '\001'
```
or
```
cd "\001"
```

See: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by NikTh on 2012-08-17
Hi , 
an other method might be to create your own mount point and mount the device there from terminal.. 
e.g: 

```
sudo umount /dev/sdb1
mkdir usbflash
sudo mount /dev/sdb1 usbflash
cd usbflash
```I assume /dev/sdb1 is the usb flash disk as listed in command 
```
sudo fdisk -l
```Thanks

---

### Post by tommyleeds on 2012-08-17
cheers sisco311 but they did'nt work i still get no such file or directory
just notice in me desktop the usb stick shows up like a little square with 00 and 01 inside.....what does that mean ?

---

### Post by steeldriver on 2012-08-17
I suspect it means it is treating the name as an octal character \001

you could try

```
cd $(echo -e "\001") 
```

if that works, you may be able to rename it to something sensible like this

```
mv $(echo -e "\001") *newname*
```(I just tried this - after creating a dir using mkdir $(echo -e "\001") - and it seemed to work) but if "\001" is the actual USB device label then remounting it like NikTh suggests may be a better option - I don't know

---

### Post by sisco311 on 2012-08-17
Please copy/paste the output of:
```
mount
```

EDIT:
Put the output of the command between [noparse]```
[/noparse] tags: 
[noparse][code]<paste the output here>
```[/noparse]

---

### Post by tommyleeds on 2012-08-18
dudes
me usb sticks are not showing up as \001 no more
if it does it again i will try those comands
cheers

---

