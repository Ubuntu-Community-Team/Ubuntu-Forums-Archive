---
title: "Howto : Automate Your Tasks With BASH Scripting"
date: 2006-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by darrenm on 2006-08-10
The main thing that draws me to Linux is the way it gives you ability to truly harness the power of your system. You can become the director of your computer and compose beautiful symphonies of automation just by understanding a little about Bash and Bash scripting.

I'm in no way a Linux guru, I've been using it for years but I've never had time to properly get into software development with Linux so even if you're new to the world of Ubuntu/Linux this guide should make sense and help you automate your tasks giving you more time to enjoy the system.
This will cover a few things including:

[list]Simple bash scripting[/list]
[list]Simple ImageMagick conversion[/list]
[list]Simple Expect scripting
[/list]

Don't let the word scripting scare you off, it really is simple and - once you understand it you will realise how your computer can do any mundane task for you quickly and efficiently.

**Our scenario:**
Random J. Newb loves his cars, he loves to fiddle with the engine and take pictures as he goes along to upload to his car forum where he can describe how difficult the front cam sprocket was to remove. He has a digital camera that he plugs into his computer running Ubuntu 6.06 Dapper. He wants to keep his photos at full size (1600x1200) but to display on the web he wants to resize them to 800x600 and compress them as JPEG files so he can upload them to his webspace via FTP. He can then toddle along to his [www.ladarivaownersclub.com](www.ladarivaownersclub.com) forum and insert the images with [img] tags.
Currently he has to open the photos using the GIMP, resize each one individually and save each one with JPEG compression to a location on his computer. Then he has to open gFTP, browse to the correct local and remote directory and send the files over. 
If it has been a long day on the car this can take a long time to do and he wonders if there can be a quicker way...

Fear not Randy, this isn't Windows(tm)

Lets get started with the basics. When the camera is connected it is automatically mounted in /media/usbdisk by Ubuntu.

Lets create a file to make our script in. You don't really need to but it doesn't hurt to know what you're going to do.

```
sudo touch /bin/picwhizz
```

this 'touches' the file into existance.

OK Heres where the meat starts.

```
cd /media/usbdisk
ls
somedodgysettingsfile.ini PICT2270.JPG  PICT2271.JPG  PICT2272.JPG  PICT2273.JPG  PICT2274.JPG  PICT2275.JPG  PICT2276.JPG  PICT2278.JPG  PICT2279.JPG

```

So we know all the files we are going to want end in .JPG (not .jpg, it matters in our world)

```

ls *JPG
PICT2270.JPG  PICT2271.JPG  PICT2272.JPG  PICT2273.JPG  PICT2274.JPG  PICT2275.JPG  PICT2276.JPG  PICT2278.JPG  PICT2279.JPG

```

Gives us only the pictures. Aha. We now know how to get a list of the correct files, thats all we need to start the script.

```
sudo gedit /bin/picwhizz
```

Lets tell the script to use bash to run. Not required but makes you feel a bit nerdy.

```
#!/bin/bash
```

The she-bang (pound-bang / hash-bang) tells bash to er, use bash to run the file.

```
MY_HOME=`echo ~`
PICS_TEMP=$MY_HOME/picstemp
FOR_WEB=$PICS_TEMP/forweb
```

This is where we set up some constants. We need something concrete to stand on before using the results in the upcoming tests. You can see we use command substitution for MY_HOME to assign it the result of "echo ~" This just prints out the home directory of the current user.

```
[ ! -d "$PICS_TEMP" ] && mkdir $PICS_TEMP
[ ! -d "$FOR_WEB" ] && mkdir $FOR_WEB
```

Wow. Deep end? Nah, lets just see what its doing. It's testing to see if the directory *~/picstemp* exists. The "-d" tells it to look for a directory and report true if its there. But wait... The exclamation mark reverses this and makes it report true if the directory does not exist. The "&&" means "do the following if true." 

So in essence the statement checks for *~/picstemp* (the ~ means your home directory) and if its not there, it creates it. Lovely.

After its done that, it does exactly the same for a directory to store the resized pics in called ~/picstemp/forweb

The next part is to move the photos into this directory. Random J. doesnt want to have to delete the photos off his camera himself so we will move them rather than just copy them.

```
mv /media/usbdisk/*JPG $PICS_TEMP
cd $PICS_TEMP
```

Simple enough. Moves anything that ends in JPG to the picstemp directory in his home then cd's into ~/picstemp.

Now it gets exciting - For loops :D. I'll loosely describe the way they work as **for ANYVARIABLE in `substitute your command here and send then output back` ; do something on that $ANYVARIABLE ; done** Perhaps the following may make sense:

```
for MYPIC in `ls *JPG` ; do convert $MYPIC -resize 800x600 -quality 75% $FOR_WEB/$MYPIC ; done
```

Go over your head? Don't worry, its easy. Read through it and decipher what its doing. Its all about substitution... 

**for MYPIC in `ls *JPG`** 
literally does ls *JPG and takes the first result. In this case PICT2270.JPG and assigns it to the variable MYPIC. So now the variable MYPIC contains "PICT2270.JPG"

**do convert $MYPIC -resize 800x600 -quality 75% forweb/$MYPIC ; done** . 
To see what this is doing just substitute the value of our variable so its really running convert PICT2270.JPG -resize 800x600 -quality 75% forweb/PICT2270JPG . This runs the imagemagick command convert (A wonderful program), resizes it to 800x600, compresses it to 75% quality and saves the resulting file in the directory *forweb/* and uses the same filename to save it.

Now the magic bit. We don't only want 1 file to be converted, we could have just typed in the filename ourselves. The for loop is called a loop because it, well, loops. Once the first iteration succeeds, it then does the whole thing again on the next line it got. Remember the *ls JPG *first result was PICT2270.JPG? Well now the 2nd line is PICT2271.JPG. Making sense? Getting a feeling of how wonderful Linux/BASH/GNU is?

It runs the convert tool on every file until there are no more and completes. 7 lines of code (1 line that actually does something meaningful) and we have got some nice smaller, compressed photos automagically from the camera (Well, Randy has anyway.)

Now we just need to make the script executable. Easy.

```
sudo chmod a+x /bin/picwhizz
```

All thats left is to run it. 

```
picwhizz
```

Depending on the amount of photos and the speed of the computer it may take a few seconds to a few minutes to convert the images. Its pretty silent but you can test it worked by going into ~/picstemp/ and running 
```
ls -alth
``` to show you the file sizes then
```
cd ~/picstemp/forweb
ls -alth
``` The files should be a lot smaller.

Now to FTP them. Shall we let the computer connect to the FTP server, log in and send the files to the correct directory and then disconnect again all by itself? For this we need a wonderful thing called expect. It does what it says, it expects things. When it gets what it expects it does something and then expects something else. When you tell it what to expect and then what to do when it gets something it expects then the world is your cloister.

I'm off to write it. Is anyone interested in this series? shall I continue?

---

### Post by ZenobiaBE on 2006-08-10
Please do continue, if the next parts are going to be as good as this one, I can't wait :D

---

### Post by kabus on 2006-08-10
> **darrenm said:**
> 
```

[ -d ! "$PICS_TEMP ] && mkdir ~/picstemp
```


You got a little typo there, it should be:

```
[ ! -d "$PICS_TEMP" ] && mkdir ~/picstemp
```

---

### Post by kabus on 2006-08-10
> **darrenm said:**
> 
```
for MYPIC in `ls *.JPG`
```



```
for MYPIC in *JPG
```

Easier and can handle filenames with spaces in them.

---

### Post by darrenm on 2006-08-10
OK, all tidied up. Teach me to do it while I'm being disturbed at work.

This is the script after you put it together to avoid confusion:

```
#!/bin/bash

MY_HOME=`echo ~`
PICS_TEMP=$MY_HOME/picstemp
FOR_WEB=$PICS_TEMP/forweb

[ ! -d "$PICS_TEMP" ] && mkdir $PICS_TEMP
[ ! -d "$FOR_WEB" ] && mkdir $FOR_WEB

mv /media/usbdisk/*JPG $PICS_TEMP
cd $PICS_TEMP

for MYPIC in `ls *.JPG` ; do convert $MYPIC -resize 800x600 -quality 75% $FOR_WEB/$MYPIC ; done

```

---

### Post by drewsimon on 2006-08-10
Yes! Please do continue this series. This is exactly the kind of thing I've been looking for.

---

### Post by Jvaldezjr on 2006-08-11
I want to add my vote for continuing.  I'm not a linux pro, but I'm not totally a newb either.  Needless to say I find this helpful in learning better linux.

---

### Post by ghowells on 2006-08-11
Yes yes, expect scripting is still somewhat of a mystery to me, please continue oh master of all that is script:razz:

---

### Post by darrenm on 2006-08-11
If you read the BASH scripting bit and thought it was pretty cool what you can do with a few tests, operators and variables then this will be the coolest thing since the Fonz's fridge.

Remember Random J. Newb wants to plug his digital camera in to his PC, press one button and a few moments later have them appear on his webspace? Well previously we wrote a script that moves the files from his camera, resizes them to 800x600 and then compresses them 75%. Finally it puts them in a directory called forweb.

To top it off, to really put the icing on the cake we should make the script connect to his ISP's FTP server, upload any files in the forweb directory and then disconnect. Making him a cup of Coffee would be nice too but thats for a later time.

Let's get started. We need a program called expect. Like Ronseal it does what it says on the tin.

```
sudo apt-get install expect
```

You should already have it really, a few things depend on it.

Before we integrate it into our earlier script we should really test to see what happens and if it's going to do the job.

```
cd ~
sudo ln -sf /usr/share/doc/expect/examples/autoexpect /usr/bin/
```

I think once you sample autoexpect you may be using it a little more so lets put it into somewhere in the path. ln -sf creates a symbolic link from /usr/share/doc/expect/examples/autoexpect to /usr/bin/autoexpect

Now get ready to work nice and tidy because autoexpect will be watching you. It may be worth a test run of logging into the FTP server and transferring files to make sure it works. Here's what I do (names changed to protect the innocent):

```
darrenm@dazlinux:~/picstemp/forweb$ ftp ftp.c*****ce.org
Connected to ftp.c*****ce.org.
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 2 of 50 allowed.
220-Local time is now 09:47. Server port: 21.
220 You will be disconnected after 15 minutes of inactivity.
Name (ftp.c*****ce.org:darrenm): w*****
331 User w***** OK. Password required
Password:
230-User w***** has group access to:  ***** 
230 OK. Current restricted directory is /
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> prompt off
Interactive mode off.
ftp> cd www/images
250 OK. Current directory is /www/images
ftp> mput *
local: PICT2740.JPG remote: PICT2740.JPG
200 PORT command successful
150 Connecting to port 12017
226-File successfully transferred
226 5.949 seconds (measured here), 17.20 Kbytes per second
...
153630 bytes sent in 6.39 secs (23.5 kB/s)
ftp> quit
221-Goodbye. You uploaded 1285 and downloaded 0 kbytes.
221 Logout.
darrenm@dazlinux:~/picstemp/forweb$
``` 

So lets do it. Deep breath...

```
autoexpect -p
```

This is where you do your own thing. Type the same commands as you normally would. For me these consist of:

cd ~/picstemp/forweb
ftp ftp.c*****ce.org
(username)
(password)
cd (remote directory)
prompt off
mput *
quit

Type exit to stop autoexpect recording. Test it works by running it

```
./script.exp
```

And sit back in amazement as it replays what you just did. If you have different files in the ~/picstemp/forweb directory than before it will FTP those instead as we are transferring with mput *

If all goes well with the autoexpect script we can integrate it into the old picwhizz BASH script we did earlier. Rename it so you know what it is and put it somewhere sensible:

```
sudo cp script.exp /usr/bin/autoftp.exp
```

And add it to the bottom of the picwhizz script (also add a cd ~ to give the expect script the same starting location as when you recorded it)

```
sudo gedit /bin/picwhizz
#!/bin/bash

MY_HOME=`echo ~`
PICS_TEMP=$MY_HOME/picstemp
FOR_WEB=$PICS_TEMP/forweb

[ ! -d "$PICS_TEMP" ] && mkdir $PICS_TEMP
[ ! -d "$FOR_WEB" ] && mkdir $FOR_WEB

mv /media/usbdisk/*JPG $PICS_TEMP
cd $PICS_TEMP

for MYPIC in `ls *.JPG` ; do convert $MYPIC -resize 800x600 -quality 75% $FOR_WEB/$MYPIC ; done

cd ~
/usr/bin/autoftp.exp

```

All being well, this will now take any files ending in JPG off the camera, move them into a folder in Randys home directory called picstemp, resize them to 800x600, compress them to 75% quality, copy them to a directory called forweb, FTP them to his webspace and then disconnect. Wow.

If we're feeling really flash we can add an icon to the panel which runs picwhizz. So then all he has to do is connect his camera, click the icon on the panel and then open firefox, type in [www.ladarivaownersclub.com](www.ladarivaownersclub.com) and get posting!

Anyone have any problems with any of this?

---

### Post by chk9 on 2006-08-17
Cool darrenm!

Now I have to go and checkout what other cool things I can do with autoexpect... :-D

---

### Post by toykilla on 2006-08-17
So where does the full size images go? Surely you don't want them in a Temp directory?

~/picstemp  (fullsize?)
~/forweb (resized)

---

### Post by DC@DR on 2006-08-17
This is a nice topic, please keep up the good work. I love scripting languages, including Bash, so would love to stick with this kinda stuff ;)

---

### Post by darrenm on 2006-08-18
> **toykilla said:**
> So where does the full size images go? Surely you don't want them in a Temp directory?

~/picstemp  (fullsize?)
~/forweb (resized)

They can go wherever you want them to go ;)

Personally I have mine setup to go to /media/hdb/mypictures/camdownload/ for fullsize and /media/hdb/mypictures/camdownload/resized for resized pics.

Part of the fun is customising it for your own setup, this script is just to show people with little experience of Bash scripting the kind of things you can do.

---

### Post by darrenm on 2006-08-18
> **chk9 said:**
> Cool darrenm!

Now I have to go and checkout what other cool things I can do with autoexpect... :-D

Anything you repeat over and over. FTPing files, SSH connecting, backing up files to a remote location etc. :)

---

### Post by hanzomon4 on 2006-08-18
Do keep this up ;)

---

### Post by MyBigToe on 2006-08-19
thankyou, this is an awesome idea, 

I just wrote  scrip to delete .Trash-username folders on my ntfs drives;
Although im too scared to try it :P

```
#!/bin/bash

MYHD=''
MY_TRASH= /$MYHD/.Trash-andrew

cd /media;
for MYHD in `ls hd*` [ -d "$MY_TRASH" ] && rm -rfv $MY_TRASH; done
```

would that work?

---

### Post by dejitarob on 2006-09-15
Thanks darrenm, expect is useful.

---

### Post by darrenm on 2006-09-17
> **MyBigToe said:**
> thankyou, this is an awesome idea, 

I just wrote  scrip to delete .Trash-username folders on my ntfs drives;
Although im too scared to try it :P

```
#!/bin/bash

MYHD=''
MY_TRASH= /$MYHD/.Trash-andrew

cd /media;
for MYHD in `ls hd*` [ -d "$MY_TRASH" ] && rm -rfv $MY_TRASH; done
```

would that work?

Sorry I didnt notice this post. No mate there is a lot of things wrong with that script.

Can you not just do:
```
sudo rm -rfv /media/hd*/.Trash-andrew
```?

---

### Post by Littleweseth on 2006-09-17
Thanks for a very informative thread.

---

### Post by zempher on 2006-11-30
What a great post!

I am most certainly a newb with anything outside of Windows, so please  stick with me!

Although very similar, here is my challenge:

I have a camera overlooking a very large university capital project.  Currently, the camera takes pictures every 15 minutes and sends them to an FTP server.  The campus content management (CMS) and FTP servers are completely different systems.  I would like to create a script that looks at the upload folder holding the pictures and finds the file with the newest accessed or created date.  Next, I need for the script to rename the picture to a specific file name and FTP it to the CMS system replacing the current pic of the project.  

I am certainly open to any suggestions and will answer any questions one might have.

Thanks for your help in advance!

---

### Post by darrenm on 2006-11-30
Hello. Should be really easy.

Lets say the folder is /var/uploads and the files are listed pic1.jpg , pic2.jpg etc.

You want to use the newest file so sort the directory listing by date then pick the top one like so:

```
#!/bin/bash
cd /var/uploads
cp `ls -alt | grep jpg | head -n 1 | awk '{print $8}'` /tmp/pic_for_cms.jpg 
/usr/bin/ftppics.exp

```

This just does commmand substitution on the bit inside the backticks, so it runs 

ls -alt - gives a dir listing in date order
grep jpg - only displays anything with jpg in the name
head -n1 - only displays the top line
awk '{print $8}' - only displays the 8th field which is delimited by spaces

and then puts the end value in the command so the command ends up as 

```
cp pic2.jpg /tmp/pic_for_cms.jpg
``` if pic2.jpg is the newest pic.

Then just go through the FTP expect bit on the first page to create an FTP expect script but call it /usr/bin/ftppics.exp, remember to chmod a+x the files.

---

### Post by zempher on 2006-12-01
Not to sound retarded, but could you explain the chmod a+x function?

Thanks!

---

### Post by darrenm on 2006-12-01
Not at all.

chmod a+x makes the files e(x)ecutable by (a)ll

---

### Post by zempher on 2006-12-06
One more question if you don't mind...

1.  How to I schedule this to run, lets say every 15 minutes....?

We ran into a few problems with the FTP process, as the FTP server only accepts connections on port 22 and has quite a bit of klugy configuration that would prevent automation.  Thus, we are building the main webpage and a "get external" function.  

So..., I have the camera pushing the files to an FTP server every 15 minutes, using each day (ex:  Fri_dec_05_2006) as the folder name.  From there, I would like to have a script that evaluates the most recent folder, take a peak inside to find the most recent .jpg, and post to the apache webserver.

Is this too hard to do?  I can't think of any other way to accomplish what it is I am trying to do.

Thanks ~ The xTreme newB.

---

### Post by darrenm on 2006-12-06
> **zempher said:**
> One more question if you don't mind...

1.  How to I schedule this to run, lets say every 15 minutes....?
run ```
crontab -e
``` then add a line such as:
```
0/15 * * * * /path/to/your_script
``` then save the text file.

> **zempher said:**
> We ran into a few problems with the FTP process, as the FTP server only accepts connections on port 22 and has quite a bit of klugy configuration that would prevent automation.  
An FTP server should never run on port 22. Port 22 should be SSH, theres absolutely no reason to run it 1 port off. I can understand running it on a high non-privileged port but moving it to 22 is pointless.

Also there shouldn't be any FTP server configuration that will stop you using an expect script. When using the prompt option it only looks for the last few characters to decide when to send commands so if things change the expect script will still work.


> **zempher said:**
> Thus, we are building the main webpage and a "get external" function.  

So..., I have the camera pushing the files to an FTP server every 15 minutes, using each day (ex:  Fri_dec_05_2006) as the folder name.  From there, I would like to have a script that evaluates the most recent folder, take a peak inside to find the most recent .jpg, and post to the apache webserver.

Is this too hard to do?  I can't think of any other way to accomplish what it is I am trying to do.

Thanks ~ The xTreme newB.No, just by using something based on the script a few posts up you should be fine. To look at the folder name and decide if it is newer takes a LOT of scripting but just sorting them into date order and picking the newest file will work fine.

---

### Post by zempher on 2006-12-11
I did a bit of research for crontab, but can't find anything concrete that points me to where the crontab is managed or how to configure the "schedule".

I got the bash script to work for moving the files, etc.  What I need to do now is run the script like so...

Mon-Fri, 0630 - 1730, every 15 minutes.

Also, where do I put this (i.e. what file) and how to initiate the scheduled process.

Thanks for your patience..., I am really new to any kernel of Linux.

---

### Post by darrenm on 2006-12-11
Every user has their own crontab. The files are stored in /var/spool/cron/crontabs but you never need to look there.

As the user you want the script to be run as (normally yourself) just run 
```
crontab -e
``` edit the file as you want. 

```
30/15 6-17 * * 1-5 /path/to/script >/dev/null
``` will work for your needs.

---

### Post by zempher on 2006-12-11
When I try to run as the logged in user, I get:

cron:  can't open or create /var/run/crond.pid:  permission denied.

So I log in as root and get the following:

cron:  can't lock /var/run/crond.pid, otherpid may be 4992:  Resource temporarily unavailable

Since I am ubuntu retarded, I haven't a clue as to what this means.

---

### Post by Bobtheknight on 2006-12-11
Hi everyone,

I've been trying to write my first scripting program.  I have these files in a folder downloaded from my cameral.  They're named something like DHC010809.JPG, DHC010910.JPG and so on.

I want to use the mv command to rename them to 1.JPG, 2.JPG 3.JPG and so on so I don't have so much hassle typing them when I want to upload them and stuff (or remember what picture is which)

Here's the code.

#!/bin/bash

NUM=1
for MYPIC in 'ls *JPG'
do  
	mv ./"$MYPIC" ./"${NUM}.JPG" 
	NUM=$NUM+1 
done

Here's the error message:

mv: target `1.JPG' is not a directory

What did I do wrong?

---

### Post by darrenm on 2006-12-12
You are using strict quotes (single ticks ' ') instead of backticks ( ` ` ) around your command substitute.

Change it to ```
#!/bin/bash
cd ~

NUM=1

# Backticks around ls *JPG

for MYPIC in `ls *JPG`
do

# You don't need the ./ as you are already in the correct dir.

mv "$MYPIC" "${NUM}.JPG"

# You can't just do NUM+1

NUM=$(($NUM+1))
done
```

---

### Post by Bobtheknight on 2006-12-12
wow thanks, it works now :D

I have two more questions:

1.  Why do I need NUM=$(($NUM+1))  Doesn't "$" return the value of the variable so all I need to do is NUM=(value of NUM) + 1.  What's the extra $ and 2 brackets for?

2.  Now I found some pictures that's saved with the format *.jpg not *.JPG.  Is there a "or" statement I can run in the for loop to make it accept both?  Because my programming teacher says cloning code is bad so I shouldn't just make 2 for loops like so:

```

#!/bin/bash

NUM=1
for MYPIC in `ls *JPG`
do  
	mv "$MYPIC" "${NUM}.JPG" 
	NUM=$(($NUM+1)) 
done

for MYPIC in `ls *jpg`
do
	mv "$MYPIC" "${NUM}.JPG" 
	NUM=$(($NUM+1)) 
done

```

Thanks a lot.

---

### Post by darrenm on 2006-12-13
> **Bobtheknight said:**
> wow thanks, it works now :D

I have two more questions:

1.  Why do I need NUM=$(($NUM+1))  Doesn't "$" return the value of the variable so all I need to do is NUM=(value of NUM) + 1.  What's the extra $ and 2 brackets for?

2.  Now I found some pictures that's saved with the format *.jpg not *.JPG.  Is there a "or" statement I can run in the for loop to make it accept both?  Because my programming teacher says cloning code is bad so I shouldn't just make 2 for loops like so:

```

#!/bin/bash

NUM=1
for MYPIC in `ls *JPG`
do  
	mv "$MYPIC" "${NUM}.JPG" 
	NUM=$(($NUM+1)) 
done

for MYPIC in `ls *jpg`
do
	mv "$MYPIC" "${NUM}.JPG" 
	NUM=$(($NUM+1)) 
done

```

Thanks a lot.
Something to do with doing the arithmetic inside the braces first then assigning rather than just adding 1 to the variable. If you do NUM=$NUM+1 you will get the variable NUM having the value 1+1 then next iteration it will have 1+1+1 etc. Check here for the syntax [http://tldp.org/LDP/abs/html/arithexp.html](http://tldp.org/LDP/abs/html/arithexp.html)

You could do it twice over or you could do it as a function then just change the JPG variable or you could regex the jpg like so:

```
ls | egrep '\<jpg$|JPG$\>' 
```

---

### Post by Bobtheknight on 2006-12-14
Thanks for the link, it will help (I think) with the next program I'm gonna write that'll help me synchronize (back up) data.  (Rsync is giving me trouble)

---

### Post by Furox on 2006-12-20
First of all , this thread is incredibly inspirational and well presented and informative, (Thanks :)  )

Im also making a script, 
what i would like to do is set up a script which converts *.daa to *.iso using poweriso 

```

#!/bin/bash
MY_HOME=`echo ~`
DAA_TEMP=$MY_HOME/daa2iso
CON_ISO=$DAA_TEMP/converted
ISO_NAME=$DAA_TEMP/*daa

[ ! -d "$DAA_TEMP" ] && mkdir $DAA_TEMP
[ ! -d "$CON_ISO" ] && mkdir $CON_ISO

cp /bin/poweriso $DAA_TEMP
mv *daa $DAA_TEMP
cd $DAA_TEMP
./poweriso convert *.daa -o $ISO_NAME.iso
rm poweriso
mv *iso $CON_ISO


```
basically the problem is that i would like to pull in the *.daa's name and attach it to the *.iso (sorry if this is confusing)

The script does its job, but theres the one flaw, and that is the outputs file name.
Any suggestions ?

p.s. is it possible to use the wget command in BASH ? (so if users dont have the poweriso file it will download it to the /bin )

Thanks

---

### Post by darrenm on 2006-12-21
Hello, thanks for the comments.

Firstly you can't dynamically assign filenames using variables. To do this will need a for file loop, something that uses another command to get the filenames at each run and substitute them for you.
```
for FILE in `ls *.daa`
do
ISO_NAME=`echo $FILE | awk -F. '{print $1}'`
/.poweriso convert $FILE -o $ISO_NAME.iso
done

```
Not sure why you are copying the poweriso out of the /bin dir? Why can't it be executed from its normal location?

Yeah you can use wget in the script, anything you do on the bash command line can be put into the script.

:)

---

### Post by Furox on 2006-12-21
> **darrenm said:**
> Hello, thanks for the comments.

Firstly you can't dynamically assign filenames using variables. To do this will need a for file loop, something that uses another command to get the filenames at each run and substitute them for you.
```
for FILE in `ls *.daa`
do
ISO_NAME=`echo $FILE | awk -F. '{print $1}'`
/.poweriso convert $FILE -o $ISO_NAME.iso
done

```
Not sure why you are copying the poweriso out of the /bin dir? Why can't it be executed from its normal location?

Yeah you can use wget in the script, anything you do on the bash command line can be put into the script.

:)


Hmm good point, (well wont can you expect when your trying to make a script around 11pm lol )
thanks for the reply, it was kind of silly to copy poweriso from /bin when i could use wget to get it,
by the way, my understanding in programming is pretty basic, 
are there any tutorials that you can recommend for bash scripting ? 
(lol not saying that this one isnt good, im looking for a more general one, )


Thanks again

---

### Post by darrenm on 2006-12-21
The Linux Documentation Project is the best one I've found. This one is very basic and only covers a few things. I'm by no means good at Bash scripting, I just use sed/awk/grep a lot

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by Furox on 2006-12-31
Me again :)
new script this time,

scenario:
I have .zip files in a download folder, which contain a animation clip each, i would like to my only those zip files (not any other zip file) and extract under a directory named Bleach, then ask the user for confirmation to delete the zip files.
the animation files are named as [Anime-Keep]_Bleach_-_01_DVD.zip (the number near the end changes as so on)

here is the script so far, and the problem is that it moves all zip files,

```

#!/bin/bash

MY_HOME=`echo ~`
MY_DOWN=$MY_HOME/Downloads
MY_BF=$MY_DOWN/Bleach

cd $MY_DOWN
mv *[Anime-Keep]*.zip $MY_BF
cd $MY_BF
tar -xf *.zip

```

Thanks

---

### Post by darrenm on 2007-01-04
> **Furox said:**
> Me again :)
new script this time,

scenario:
I have .zip files in a download folder, which contain a animation clip each, i would like to my only those zip files (not any other zip file) and extract under a directory named Bleach, then ask the user for confirmation to delete the zip files.
the animation files are named as [Anime-Keep]_Bleach_-_01_DVD.zip (the number near the end changes as so on)

here is the script so far, and the problem is that it moves all zip files,

```

#!/bin/bash

MY_HOME=`echo ~`
MY_DOWN=$MY_HOME/Downloads
MY_BF=$MY_DOWN/Bleach

cd $MY_DOWN
mv *[Anime-Keep]*.zip $MY_BF
cd $MY_BF
tar -xf *.zip

```

Thanks

Sorry for the delayed reply.

escaping the [ and ]

```
mv \[Anime-Keep\]*.zip $MY_BF
```

should sort you :)

---

### Post by Furox on 2007-01-04
ahh thanks,

---

### Post by Ahriman on 2007-02-10
Awesome thread, thanks for taking the time to write this How-to.

I have looked in my system for autoexpect, and whilst I have expect installed, I cannot find autoexpect at all. Looking in /usr/share/docs/expect I don't seem to have a "examples" directory. Any thoughts on where I can get this back, or reinstalled?

---

### Post by q335r49 on 2007-02-10
Interesting thread.  I have a question: How do I automate sudo tasks (e.g. wifi-radar?)
For awhile 

echo password|sudo wifi-radar

Seemed to work, now it doesn't.  Any suggestions?

---

### Post by darrenm on 2007-02-10
> **Ahriman said:**
> Awesome thread, thanks for taking the time to write this How-to.

I have looked in my system for autoexpect, and whilst I have expect installed, I cannot find autoexpect at all. Looking in /usr/share/docs/expect I don't seem to have a "examples" directory. Any thoughts on where I can get this back, or reinstalled?

The latest packages don't seem to include it. Autoexpect is just an expect script itself so just download it from [here]("http://expect.nist.gov/example/autoexpect") and put it anywhere you like, chmod it +x and run it as described.

---

### Post by darrenm on 2007-02-10
> **q335r49 said:**
> Interesting thread.  I have a question: How do I automate sudo tasks (e.g. wifi-radar?)
For awhile 

echo password|sudo wifi-radar

Seemed to work, now it doesn't.  Any suggestions?

Try ```
echo "password" | xargs sudo wifi-radar
``` :)

---

### Post by q335r49 on 2007-02-10
aaa interesting, that seemed to work.  Thanks!

---

### Post by shak on 2007-02-10
Thank you very much for this thread. This is a lot fun!
I forgot a about the magic of the shell.

Regarding the examples. I had an issue with the examples not installing with expect too. Something is borked inside the repositories since a few days. (mesa and libgl for example, but thats another story)

Thankfully there is an alternative as everytime expected ;)

```
 
sudo apt-get install expect-tcl8.3

```

will do the job exactly and brings the scripts with it.

kind regards

---

### Post by thejart on 2007-02-13
darrenm, thanks for the how-to!  i found this thread yesterday and after reading your first post i decided to tackle a problem that i've had for a while.  you see, i have a sizable collection of live music in flac format (and also in shn format, but that's another story/script).  the problem is i can't play them on my ipod (well, i guess i could if i wanted to do some hacks and sacrifice battery life).  so, long story slightly shorter, i needed a script to:

-look in my ~/my_sounds/flac/not_mp3d directory for directories containing flacs
-encode them and put the mp3s in my ~/my_sounds/mp3/to_ipod directory
-then move the flac-containing directory to my ~/my_sounds/flac/mp3d directory

here it is:

> #!/bin/bash

# This script looks at the "/home/thejart/my_sounds/flac/not_mp3d" directory and
# mp3 encodes all of the flac files and saves them to the "~/my_sounds/mp3/to_ipod"
# directory.  It is assumed that the flac files are inside of a show or albumn 
# directory, which is moved in its entirety to the "~/my_sounds/flac/mp3d" directory.


# Setup environment
HOME=/home/thejart
MUSIC_DIR=$HOME/my_sounds
FLAC_DIR=$MUSIC_DIR/flac/
MP3_DIR=$MUSIC_DIR/mp3/to_ipod


# Increment through the folders and files and convert the flacs over to mp3z
# then move the directories to the flac/mp3d directory
cd $FLAC_DIR/not_mp3d
for TMP_FLAC_DIR in `ls -d */` ; do 
 [ ! -d "$MP3_DIR/$TMP_FLAC_DIR" ] && mkdir $MP3_DIR/$TMP_FLAC_DIR
 for TMP_FLAC_FILE in `ls $TMP_FLAC_DIR*flac` ; do 
  flac -d -o - $TMP_FLAC_FILE | lame -b 224 -h --noreplaygain - $MP3_DIR/$TMP_FLAC_FILE.mp3 ; 
 done ;
 mv -t $FLAC_DIR/mp3d/ $FLAC_DIR/not_mp3d/$TMP_FLAC_DIR 
done

exit 0

...and it works.  the problem is when i set up my crontab to run it every night, it doesn't.  it encodes one file and moves the flac directory to ...flac/mp3d and quits.  i know that you are supposed to use full paths within cron jobs and looks like i am.

any suggestions?

here's my crontab:
> 0 1 * * * /home/thejart/my_sounds/.flac2mp3.sh

---

### Post by darrenm on 2007-02-14
Well lets substitute the variables in:

Lets say one of the directories it picks up is called tmp1

```

cd /home/thejart/my_sounds/flac/not_mp3d
for TMP_FLAC_DIR in `ls -d */` ; do
#
# $TMP_FLAC_DIR will be set to tmp1/
#
[ ! -d "/home/thejart/my_sounds/mp3/to_ipod/tmp1/" ] && mkdir /home/thejart/my_sounds/mp3/to_ipod/tmp1/ && echo $TMP_FLAC_DIR
#
#We're in a folder called flac/not_mp3d, the variable $TMP_FLAC_DIR only has tmp1/ as the value. So the next for loop won't work. 
#
for TMP_FLAC_FILE in `ls tmp1/*flac` ; do
flac -d -o - $TMP_FLAC_FILE | lame -b 224 -h --noreplaygain - $MP3_DIR/$TMP_FLAC_FILE.mp3 
echo $TMP_FLAC_FILE
done ;
mv -t $FLAC_DIR/mp3d/ $FLAC_DIR/not_mp3d/$TMP_FLAC_DIR
done

exit 0
```

Sorry for the time replying. Hopefully this will help. To start off if you're having problems its better to use the actual paths rather than variables then change for variables to make it portable.

Also try echo'ing the variable after every time you use it to make sure it contains the correct data.

---

### Post by thejart on 2007-02-14
thanks for getting back to me, darrenm.  i've rewritten the script and replaced all of the commands (mkdir, flac|lame, and mv) to echos of what they would be doing, just to make sure that the directories are being traversed correctly.  i ran the script both manually and as a cronjob with the output being redirected to a file.  the script works both ways.

you had commented that the second loop wouldn't work.  you may have thought that i was using the same variable twice, but i'm not.  there's a tmp_flac_dir and a tmp_flac_file.

anyway, i'm beginning to think that the issue is in my crontab syntax.  do i need special syntax for a job that runs for much longer than a minute?

---

### Post by darrenm on 2007-02-15
Weird. I've set up the same dir structure as you and the script runs fine. Does it run fine for you when run manually (not from cron)?

Make sure you haven't got the dir its trying to create at the mv command already there.

Dang it! You're right, I've just tried it from cron and its doing what you described. This is bizarre. I'm on the case ;)

---

### Post by thejart on 2007-02-15
i've asked a friend of mine who's been using linux a lot longer than me for some help too.  if i find out anything i'll let you know.

btw, and i think you've already figured this out, yes, the script works fine when run manually.  and i haven't run it when the dir already exists as the mv command is trying to do its thing.

thanks again!

---

### Post by thejart on 2007-02-15
ok, got it.  my friend suggested that i send stderr to the logfile as well.  my crontab entry changed to:

07 11 * * *     /home/thejart/my_sounds/.flac2mp3.sh > flaclog 2>&1

it was obvious at that point that my environment wasn't properly setup...it couldn't find 'ls'

i added:
PATH=/usr/bin:/usr/bin/X11:/bin  #i added the lame and flac paths too

to the beginning of the crontab and now it works.  woohoo!  i've noticed that a lot of people seem to have issues when running stuff via cron.  i bet this causes the bulk of their problems too.

---

### Post by darrenm on 2007-02-15
Excellent. I'm sure you're right about the cron env not being set correctly on other systems too.

---

### Post by Jarn on 2007-03-25
Is there a way to prompt for input in a script? Like, prompt for version and store their reply in variable VERSION?

---

### Post by darrenm on 2007-03-26
yep its just ```
read VERSION
```

Then you can use case to do different things depending on the variable: ```
case $VERSION in;
1|1.1|1.2) echo "$VERSION is in the V1 release";;
2|2.1|2.2) echo "$VERSION is in the V2 release";;
q|Q|e|E|x|X) exit 0;;
*) echo "That is not a valid entry";;
esac
```

---

### Post by Jarn on 2007-03-26
> **darrenm said:**
> Then you can use case to do different things depending on the variable: ```
case $VERSION in;
1|1.1|1.2) echo "$VERSION is in the V1 release";;
2|2.1|2.2) echo "$VERSION is in the V2 release";;
q|Q|e|E|x|X) exit 0;;
*) echo "That is not a valid entry";;
esac
```

Is there a way to have it execute multiple commands in the case besides using &&? Like if I wanted to have it ```
echo "$VERSION is in the V1 release" && echo "That's a shame!"
``` or something like that. Is there a way to do it without the double ampersands?

Btw, bash didn't like the semi-colon at the end of the case line, but it worked when I took it out.

---

### Post by darrenm on 2007-03-27
Yeah just use ```
echo "$VERSION is in the V1 release"; echo "Thats a shame!"; FAILED=1; MENU;;
```

---

### Post by Jarn on 2007-03-27
Thanks!

---

### Post by eecharlie on 2007-04-01
I keep seeing this all over the place and it drove me nuts until I read the right way to do it, so I'm going to post this here:  

Using the following to implement a for loop is bad:

for $X in `ls *JPG`

Because when bash parses the output of a command, in this case ls, **all carriage returns are stripped and all whitespace is treated as element delimiters**. This means that filenames with spaces will be separated into multiple separate filenames and the script will break. 

Instead, try

for $X in *JPG

In this case bash evaluates the regular expression *JPG to find the directory listing directly instead of using an external command, thus avoiding the whitespace issue.

I'm new to bash myself, so I don't know of a solution to this, but using JPG is also fragile because (I think) it will be case-sensitive.

Cheers,
Charlie

---

### Post by darrenm on 2007-04-01
Yep you're right. I keep typing it by mistake on force of habit.

The regex for either case is *[JjPpGg]

---

### Post by Blindraven on 2007-07-30
It's a great post but I think anyone reading should most definitely check out 
[[IMG]http://www.linuxcommand.org/images/lc2_logo_1.jpg[/IMG]](http://www.linuxcommand.org)

That way you understand exactly what you are doing, what commands are parsed, various ways of invoking them, and most importantly ;

Actually understanding how things works under the hood.

Once you have the basics down pat and you know the fundamentals you are only limited by your own imagination, and if your browsing a *nix forum looking at how to write or automate scripts you've done far more then most "PC" users ever would have.

Kudos +10.

---

### Post by darrenm on 2007-07-31
Very nice site! I think that in combination with the bash scripting guide at [www.tldp.org](www.tldp.org) should cover almost everything anyone needs to know.

---

### Post by renkinjutsu on 2009-02-03
sorry to revive such an old thread
but Darrenm, you seem to be so helpful

I actually tried writing a script to sync files with my dropbox folder.. 

```
pdir=`echo ~/Pictures`
wrdl=$pdir/word
wrdd=$pdir/Wordle/Dumb\ Slut\'s

for pix in *.* ; do [ ! -f $wrdd ] && ln -vs $wrdl/"$pix" $wrdd ; done
```

I made this because I'm very picky about where I have my files. . . i prefer to have my images somewhere in my Pictures folder
and i also don't want dropbox to have access to hard copies of my images, in case someone on the intarweb decides to delete them..  Also, i wanted to save space and use symbolic links instead of making actual copies of the file.

I tried those commands in the command line and it seems to work
but as soon as i run the script, it returns with the error: 
> [: 5: Slut's/: unexpected operator
it's just a few lines and i can't even see where i went wrong!

---

### Post by darrenm on 2009-02-04
Hi. It's because the space in the directory is making the test think you are passing it an extra parameter. Just enclose the directory in double quotes eg.

ppdd="/some dir with spaces/"

If you quote a path you don't need to escape the space. Hope this helps.

posted from android

---

### Post by johnraff on 2009-02-04
You might want to quote all your variables when you call them, to be on the safe side:```
for pix in *.* ; do [ ! -f "$wrdd" ] && ln -vs "$wrdl"/"$pix" "$wrdd" ; done
```

btw another resource I've got all kinds of good advice from:[BashFAQ - Greg's Wiki](http://wooledge.org:8000/BashFAQ?action=show&redirect=BashFaq)

---

### Post by renkinjutsu on 2009-02-05
Thanks! the double quoting worked!
I thought everything would work if i tested it to be okay with "cd" in the terminal first

.. it cd'd to my directory, so i thought the syntax was correct.. is it different for different commands in the terminal?

---

### Post by RyconPayne on 2009-04-09
Hello, I'm fairly excited about the fact that I've made my first shell script.  Sure, it is a Frankenstein of various other shell scripts I have found on the net, so it's not completely "mine", but I'm proud anyway.  

I've used dropbox since the beginnings of it's beta testing, and I've always loved it.  The only problem I've ever had was that I had to copy the file, paste it into my drop box, right click on the file, get the public link.  Too many steps, and I couldn't find anyone that had made it easier.

I first asked on these forums for help, and never got a response.  Maybe I did it in the wrong forum, or thread, but I decided to jump in and try myself.  Here's what I came up with at first:

Create a nautilus action with the parameters %d %f and the path pointing to this script:

```
#!/bin/bash

#Set Variables
#
#Dropbox's Public directory
public="/dir/to/Dropbox/Public"

#In your dropbox public URL, the numbers found after /u/
number="0000000"

#Copy files to the Public directory, and send the URL to the clipboard
cp $1/$2 $public
text="http://dl.getdropbox.com/u/$number/$2"
echo -n "$text" | xsel -ib  ## xclip -i -f -selection "clipboard"
```

This will copy a single file to dropbox's public folder, and send the public link to your clipboard.

This wasn't good enough though, as I usually am copying several files at a time.  The next script was much more frustrating to make, but I'm very proud of it :D


```
#!/bin/bash

#Set Variables

#Dropbox's Public directory
public="/dir/to/Dropbox/Public"

#In your dropbox public URL, the numbers found after /u/
number="0000000"

#Create a file to send the URLs to, then put the path to that file here
urlfile="/home/username/temp/dropbox"

dir=$1

#  Copy files to Dropbox and create file with Public URL for files
(while [ $# -gt 0 ]; do
	cp $dir/$2 $public	
	echo "http://dl.getdropbox.com/u/$user/$2" >> $urlfile
	shift
	done
)

#  Remove blank line at the top of output file, as well of the last line that for some reason is just the URL without a filename.
mv $urlfile $urlfile.tmp
sed '/^$/d;$d' $urlfile.tmp > $urlfile
rm $urlfile.tmp

#  Copy contents of file with URLs to the clipboard.

cat $urlfile | xsel -ib  ## xclip -i -f -selection "clipboard"

#Clear file of links

cat /dev/null > $urlfile
```

I've tested this a bit, and made some changes.  I don't know if you can do this cleaner, or better than this.  I don't know if there's some problem with this I haven't figured out or encountered yet.  I'm proud anyway. 

If someone does see something I did that can be done better, please speak up.  I'd love to learn more.

---

### Post by renkinjutsu on 2009-04-10
I wrote a script so that I can specify a time I want to run a specific command or set of commands.  I didn't want to use crontab since it wasn't something i wanted to repeat in a pattern, this is just for the on the go, set a command thing..
currently, it only works if you type in one command, but if you want to type in more than one command, type in "nan" when prompted for a command

the problem i'm having is that bash isn't handling the numbers with a 0 in front of it.. example would be $(( 17 - 08 )) would give an error with the error token at 08.  I can't think of any other way to write this script though

```
echo " input a command"
read -p "  -- " comm

if [ "$comm" = nan ] ; then
	touch schedexec
	echo "#!/bin/bash" >> schedexec
	nano schedexec
	echo "rm -v \"\$0\"" >> schedexec
	chmod +x schedexec
fi

echo " time: hours :: 24hr format"
read -p "  -- " shour
echo " time: minutes"
read -p "  -- " sminute

r=0
while [ $r = 0 ] ; do
	now=`date +%H%M`
	nhour=`date +%H`
	nminute=`date +%M`
	nsec=`date +%S`

	if [ $now = $shour$sminute ] ; then
		notify-send -t 200000000 -i ~/Pictures/melonn.png "Scheduled task" "schedcom tasks started"
		if [ "$comm" = nan ] ; then
			bash schedexec
		elif [ ! "$comm" = nan ] ; then
			$comm
		fi
		r=1
	elif [ $now -lt $shour$sminute ] ; then
		if [ $(($sminute-1)) = $nminute ] ; then
			clear
			echo ; echo ; echo ; echo ; echo
			echo " $((60-$nsec))   seconds"
		elif [ $nminute -lt $sminute ] ; then
			clear
			echo ; echo ; echo ; echo ; echo
			echo " $(($shour-$nhour))   hrs     $(($sminute-$nminute))   mins"
		elif [ $nminute -ge $sminute ] ; then
			clear
			echo ; echo ; echo ; echo ; echo
			echo " $(($shour-$nhour-1))   hrs     $((60-$nminute+$sminute))   mins"
		fi
	elif [ $now -gt $shour$sminute ] ; then
		echo Specified time has already passed, please try again.
		read -p "Press [Enter] to restart"
		gnome-terminal -e "$0"
		exit
	fi

	sleep 1
done
notify-send -t 2000000000 -i ~/Pictures/melonn.png "Scheduled task" "schedcom tasks completed"
```

---

### Post by trace02 on 2010-09-24
I can not get this code to work when more than one file is returned.  I get the following error:
cp: missing destination file operand after `/interfaces/lrhyperi/bsc2agency/hctst/data/b_bd009i_act.txt'

Here is my code cp `ls -alt | grep "b_bd009i_act_2*.TXT" | head -n 1 | awk '{print $8}'` /interfaces/lrhyperi/bsc2agency/hctst/data/b_bd009i_act.txt 
 
Please help
 
Thanks

---

