---
title: "Code::Blocks permission denied"
date: 2012-04-13
forum: Programming Talk
---

### Post by 8163jb on 2012-04-13
Hey, I am a newbie to all this and I have just installed code::blocks. When I try to compile and run simple programs it gives me the error message 'sh: /path/to/my/file: permission denied'. I have read around a bit and tried varous solutions from other forums but none seem to work. I am running ubuntu 10.4. Any help? Cheers

---

### Post by dniMretsaM on 2012-04-13
Make sure you're the owner of the files. If you're not, you can run this:
```
sudo chown usrname:username /path/to/your/file
```

Also make sure it's executable:
```
chmod +x /path/to/your/file
```

---

### Post by 8163jb on 2012-04-13
Cheers, but the usrname:username code doesn't seem to work??? I have replaced the bit which says username with my username but it still doesn't do it???

---

### Post by 8163jb on 2012-04-13
> **dniMretsaM said:**
> Make sure you're the owner of the files. If you're not, you can run this:
```
sudo chown usrname:username /path/to/your/file
```Also make sure it's executable:
```
chmod +x /path/to/your/file
```

Got that code to work now but it still shows the same error message? Any other Ideas? Cheers

---

### Post by raja.genupula on 2012-04-13
> **8163jb said:**
> Hey, I am a newbie to all this and I have just installed code::blocks. When I try to compile and run simple programs it gives me the error message 'sh: /path/to/my/file: permission denied'. I have read around a bit and tried varous solutions from other forums but none seem to work. I am running ubuntu 10.4. Any help? Cheers

in which partition it was saved ? 
EXT or FAT,NTFS ?

---

### Post by 8163jb on 2012-04-13
> **raja.genupula said:**
> in which partition it was saved ? 
EXT or FAT,NTFS ?
I don't know? How would I find out?

---

### Post by raja.genupula on 2012-04-14
where you have saved that file ?  Home directoy or some other partitions of your HDD

---

### Post by r-senior on 2012-04-14
> **8163jb said:**
> Got that code to work now but it still shows the same error message? Any other Ideas? Cheers
Can you find the file using the file manager? (It's called Nautilus).

Right-click on it and choose Properties. Then go to the Permissions tab.

It should show that you are the owner of the file and that you have read and write access. Also, if you want to run it as a program, that the "Allow executing file as program" box is checked.

The commands you were typing were:

```
chown username.groupname <filename>
```

This sets the owner and group of a file to username and groupname respectively.

```
chmod +x <filename>
```

This adds execute permissions (for owner, group and world).

---

### Post by itsols on 2012-05-13
> **raja.genupula said:**
> in which partition it was saved ? 
EXT or FAT,NTFS ?

Your question makes sense. I had the SAME problem when running Code::Blocks on Ubuntu and my source folder was on an NTFS partision.

I could not do any permission changes there either - naturally, it's not EXT.

I solved it by keeping my cpp project files in the same partition as Ubuntu (having EXT) and it works now.

Hope others benefit by this :)

---

### Post by xadix on 2013-02-10
simple way I've ... 
You just open a new file using ( Ctrl + Shift + N )
Than save it using ( Ctrl + S )
Than name it *** And after the name Just put ( .cpp ) ***

Thats all .. 
Do programming and Run ..
Have Fun ...

 :guitar:

---

