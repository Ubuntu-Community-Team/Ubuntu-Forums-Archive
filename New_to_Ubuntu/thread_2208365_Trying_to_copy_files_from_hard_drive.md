---
title: "Trying to copy files from hard drive"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by muzi2 on 2014-02-27
my 2010 iMac hard drive went down. I need the iPhoto and iMovie files......so after research, I made a ubuntu CD to start up the computer, under Ubuntu, I can see my hard drive, but I couldn't open my pictures and movies folder. once I click on the movie folder, it says, I don't have permissions necessary to view the contents of "movies". 

so I did some research, it is my understanding i could make copy with the sudo cp command?  so I typed 

sodu cp -r /media/macintosh hd/users/muzi/pictures* /media/freeagent go flex drive/muzi/

however i get an error message "target 'drive/' is not a directory. 


how could I make copies of the pictures and movies in iPhoto and iMovie????? 
Thank you so much for your help. I know nothing about computer. I really could't figure this out by researching online ..
thank you thank you.

---

### Post by sandyd on 2014-02-27
moved to Absolute Beginners Section
try
```

sudo cp -R "/media/macintosh hd/users/muzi/pictures"* "/media/freeagent go flex drive/muzi/"
```

Linux doesnt like spaces in directory names - putting double quotes around it fixes that

---

### Post by muzi2 on 2014-02-27
Thank you very much.   I tried, now I have another error message, 

'media/macintosh hd/users/muzi/pictures*': no such file or directory.

Am I wrong that this is the location where my iPhoto pictures are saved?

---

### Post by sandyd on 2014-02-27
Linux is case sensitive, try 'Macintosh HD' instead of macintosh hd

Also, can you post the output of
```

mount -l
```

Thanks!

---

### Post by muzi2 on 2014-02-27
I used su nautilus. and I don't know what I did.....now I can see the content of pictures and movies folders , but can't open any of the files.. 


and sorry, i don't know how to do this in your format ...let me see if i could find where to learn that.

---

### Post by sandyd on 2014-02-28
> **muzi2 said:**
> I used su nautilus. and I don't know what I did.....now I can see the content of pictures and movies folders , but can't open any of the files.. 


and sorry, i don't know how to do this in your format ...let me see if i could find where to learn that.

can you post the output of
```

mount -l
```

---

