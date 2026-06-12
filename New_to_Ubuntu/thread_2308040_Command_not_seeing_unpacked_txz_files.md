---
title: "Command not seeing unpacked txz files"
date: 2015-12-30
forum: New to Ubuntu
---

### Post by Binman278 on 2015-12-30
I am installing Cinelerra 5.0 and the download is in the form of two files .txz & .txz.1
 

 the vague instructions say download unpack and enter the command /opt/cinelerra/cinelerra.
 

 I dont fully understand what I need to do &#8220;to&#8221; unpack these compressed files, I seem to have done this as I have a Folder  /home/Binman/cinelerra/extracted_files/ that now contains 5 Folders named: locale, doc, plugins, ffmpeg & models. Then the two .txz files one marked XZ Compressed, and several other files including a PDF manual.  

 

 If I now enter the command /opt/cinelerra/cinelerra it says File does not exist which it clearly does but not where the Terminal is looking. What do I need to do to get it to work? 

 

 Thanks

---

### Post by papibe on 2015-12-30
Hi Binman278.

'Download / Unpack' seems to be the tittle of the instructions, but somehow ended up on the code section (as if it were a command).

I would recommend installing cinelerra from a ppa. Here are the instructions: [step-to-step-how-to-install-cinelerra]("http://askubuntu.com/questions/67164/step-to-step-how-to-install-cinelerra")

Hope it helps. Let us know how it goes.
Regards.

---

### Post by leunam12 on 2015-12-31
This is what you are supposed to do:
1- Create a new directory in /opt named cinelerra
```
sudo mkdir -p /opt/cinelerra
```

2-Go to /opt/cinelerra
```
cd /opt/cinelerra
```

3-Download the cinelerra package
```
sudo wget -P `pwd` http://cinelerra.org/2015/downloads/cinelerra-5.0-ubuntu-14.04.1-x86_64-20151221-static.txz
```

4-Unpack the recently downloaded package.
```
sudo tar -xJf cinelerra-5.0-ubuntu-14.04.1-x86_64-20151221-static.txz
```

(Off-topic: I could not place the last line between code brackets because it gives me an error, I tried it several times and it always splits it in two lines) 
(Fixed it - sandyd)

---

### Post by leunam12 on 2015-12-31
I tried it and almost everything worked for me. This is what I had to change:

1-I used 7zip instead of tar because tar gave me an error. 
```
sudo 7za x cinelerra-5.0-ubuntu-14.04.1-x86_64-20151221-static.txz
```
this extracts to a tar file: cinelerra-5.0-ubuntu-14.04.1-x86_64-20151221-static.tar
then:
```
sudo 7za x cinelerra-5.0-ubuntu-14.04.1-x86_64-20151221-static.tar
```

2- I had to change the the ownership of /opt/cinelerra to my own user
```
sudo chown -R myownuser /opt/cinelerra
```
myownuser is your user name, of course.

3- I had to make the file cinelerra executable
```
chmod +x /opt/cinelerra/cinelerra
```
Now it works.

---

### Post by Binman278 on 2015-12-31
Hi Papibe,

Thanks for the prompt reply. I should have said I was up grading from Cinelerra CV to Cinelerra version 5.0. Previously I had installed the CV version using a ppa and instructions very similar to your link and all worked. I later found version 5.0 would better suit my requirements hence the upgrade. Thank you for taking the trouble to reply though,
Regards Binman

---

### Post by Binman278 on 2016-01-01
Hi Leunam 12, Happy New Year,
 

 I have tried to do as you instructed and have failed!!
 

 I do now have an /opt folder in the &#8220;File system&#8221; and this has one folder named Cinelerra, this folder has several other folders, the txz file and a load of other items I would expect like a manual and some PNG files etc. So I take it the file unpacked. So far so good.
 

 So then I referred to your second posting. The first part I think in effect has been done. The second part I have failed to get to work.  
 

 

 

 **next:  [FONT=Liberation Serif, serif][SIZE=3]I had to change the the ownership of /opt/cinelerra to my own user[/SIZE][/FONT]**
 sudo chown -R myownuser
/opt/cinelerra   **(**[FONT=Liberation Serif, serif][SIZE=3]**myownuser is your user name, of course.)**[/SIZE][/FONT] 

[FONT=Liberation Serif, serif][SIZE=3]sudo chown -R [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]name[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]/opt/cinelerra  [/SIZE][/FONT]


 Then This Showed
 

 name@name-SR-0110:~$ sudo chown -R name /opt/cinelerra 
 [sudo] password for name:  (entered my password and pressed enter)
 name@name-SR-0110:~$ 
 

  **[FONT=Liberation Serif, serif][SIZE=3]3-I had to make the file cinelerra executable[/SIZE][/FONT]** [FONT=Liberation Serif, serif][SIZE=3]chmod+x /opt/cinelerra/cinelerra  [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]([/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]entered this [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]then this showed)[/SIZE][/FONT] 

 name@name-SR-0110:~$ sudo chown -R name /opt/cinelerra 
 [sudo] password for name:  (entered password)
 name@name-SR-0110:~$ chmod +x /opt/cinelerra/cinelerra 
 name@name-SR-0110:~$ 
 

 As no errors or messages about problems showed I thought it had worked. However I cant find it.
 When I installed Cinelerra CV from a ppa on a previous occasion I went to the search section and typed in Cinelerra and the programe was there but on this occasion it is not. What do you make of it? (For some reason this reply has re formatted the font and spacings in the posting)

 

 Regards

---

### Post by leunam12 on 2016-01-01
now open the terminal and type:```
/opt/cinelerra/cinelerra
```and press enter.
If it works then create a launcher so you don't have to open via terminal anymore.
If it doesn't work open terminal and type:```
ll /opt/cinelerra
``` and post the results here.
In my computer it looks like this: ```
rivasdom@RivasPC-2:~$ ll /opt/cinelerra
total 181708
drwxr-xr-x  7 rivasdom root     4096 Dec 31 06:34 ./
drwxr-xr-x  8 root     root     4096 Dec 31 06:10 ../
-rw-r--r--  1 rivasdom root 93494868 Dec 21 16:14 bdwrite
-rwxr-xr-x  1 rivasdom root 38158216 Dec 21 16:15 cinelerra*
-rw-r--r--  1 rivasdom root    17989 Dec 21 16:16 COPYING
-rw-r--r--  1 rivasdom root  6067683 Dec 21 16:14 cutads
drwx------  2 rivasdom root     4096 Dec 31 06:32 doc/
drwx------  5 rivasdom root     4096 Dec 31 06:32 ffmpeg/
drwx------ 17 rivasdom root     4096 Dec 31 06:32 locale/
-rw-r--r--  1 rivasdom root  7249472 Aug  6 19:21 manual.pdf
drwx------  2 rivasdom root     4096 Dec 31 06:32 models/
-rw-r--r--  1 rivasdom root  4856776 Dec 21 16:16 mpeg31trkpony
-rw-r--r--  1 rivasdom root  4978061 Dec 21 16:16 mpeg3cat
-rw-r--r--  1 rivasdom root  4987884 Dec 21 16:16 mpeg3cc2txt
-rw-r--r--  1 rivasdom root  4968095 Dec 21 16:16 mpeg3dump
-rw-r--r--  1 rivasdom root  4863994 Dec 21 16:16 mpeg3ifochk
-rw-r--r--  1 rivasdom root  4960681 Dec 21 16:16 mpeg3peek
-rw-r--r--  1 rivasdom root  4852742 Dec 21 16:16 mpeg3show
-rw-r--r--  1 rivasdom root  4963782 Dec 21 16:16 mpeg3toc
-rw-r--r--  1 rivasdom root  1107872 Dec 21 16:08 mplex
-rw-r--r--  1 rivasdom root     8885 Oct 31 13:26 msg.txt
-rw-r--r--  1 rivasdom root   468282 Dec 21 16:16 new_db
drwx------ 16 rivasdom root     4096 Dec 31 06:35 plugins/
-rw-r--r--  1 rivasdom root       57 Dec 21 16:16 README
```

---

### Post by leunam12 on 2016-01-01
I cannot tell you how to create a launcher because I don't use Unity and I am not familiar with the procedure. I imagine that all you have to do is create a .desktop file and then drag it to the launcher bar, but I am not sure.

---

### Post by Binman278 on 2016-01-02
Hello leunam 12,

ll /opt/cinelerra worked and Cinelerra 5.0 opened. I had a bit of trouble trying to create a launcher and gave up! Some research showed it isnt as simple as many make out because Cinelerra (and other additional applications) do not go into the folder 14.04 expects and to sort it out was looking very complex. Cinelerra must know about this. So I tried it just from the terminal launch and it is all there but it crashes the pc when I try to load files which is some bug within it. No doubt they will sort it out over a long time, meanwhile I will use the CV version Cinelerra say is "crap" which actually works very well!!!! So much for progress. Thanks VERY much for your assistance in this matter, I learnt many things.

---

### Post by leunam12 on 2016-01-04
You are welcome.

---

