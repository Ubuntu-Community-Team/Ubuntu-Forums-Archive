---
title: "Add Progress Bar to Bash script?"
date: 2007-08-15
forum: Programming Talk
---

### Post by brennydoogles on 2007-08-15
So How do you? I am trying to touch up a script that i wrote a while back, and a progress bar would go a long way toward helping make the script easier to use. Thanks for the help!!

---

### Post by Sp4cedOut on 2007-08-16
if by progress bar you mean something like:

(================================)

there are a few ways you could do it, I'm not sure what to recommend without knowing more about your program.

The simplest example I can think of is, let's say your program can be divided into 20 different steps, you could just print out an equal sign for each step.

A more complicated one would be if you're trying to download a file, since your program would probably be suspended during the download you'd need to fork() the execution and have it output = signs representative of the percentage of the file is downloaded.

---

### Post by brennydoogles on 2007-08-16
> **Sp4cedOut said:**
> if by progress bar you mean something like:

(================================)

there are a few ways you could do it, I'm not sure what to recommend without knowing more about your program.

The simplest example I can think of is, let's say your program can be divided into 20 different steps, you could just print out an equal sign for each step.

A more complicated one would be if you're trying to download a file, since your program would probably be suspended during the download you'd need to fork() the execution and have it output = signs representative of the percentage of the file is downloaded.

This would actually be to monitor the progress of the dd command. I will attach the script I am updating if that helps. Thanks for the help!!

---

### Post by cwaldbieser on 2007-08-16
> **brennydoogles said:**
> So How do you? I am trying to touch up a script that i wrote a while back, and a progress bar would go a long way toward helping make the script easier to use. Thanks for the help!!

This utility might help [http://clpbar.sourceforge.net/]("http://clpbar.sourceforge.net/").

---

### Post by brennydoogles on 2007-08-16
> **cwaldbieser said:**
> This utility might help [http://clpbar.sourceforge.net/]("http://clpbar.sourceforge.net/").

It looks like what I would need, but I am unsure as to how I would need to integrate it into my script. Any suggestions??

---

### Post by aysiu on 2007-08-16
Have you thought about using Zenity?
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by s1ightcrazed on 2007-08-16
In *theory* all you need to create a progress bar is:

start
current
end

I.E. - with dd you are most likely going to be using file size to determine progress. Start will be 0, current will be the current size of the file, and end will be the final size of the file. You could use a tool like du to find the size of the file as it is being created, and hopefully you can do the same on the DVD to find the total size of the file. Then, inside your script you need to have a loop that will look at the current size of the file as opposed to the final size, calculate a 'percentage complete' and then use that to determine how much of the progress bar to show. 

Hope that gives you a starting point. I can whip up some code if you want an example.

---

### Post by cwaldbieser on 2007-08-16
> **brennydoogles said:**
> It looks like what I would need, but I am unsure as to how I would need to integrate it into my script. Any suggestions??

I think you would just replace your "dd" command with something like:
```

dd if="$INFILE" | ./bar -s $EXPECTED_SIZE | dd of="$OUTFILE" ;

```
There seem to be a slew of options to the utility (try ./bar -h 2>&1 | less).

---

### Post by brennydoogles on 2007-08-16
> **cwaldbieser said:**
> I think you would just replace your "dd" command with something like:
```

dd if="$INFILE" | ./bar -s $EXPECTED_SIZE | dd of="$OUTFILE" ;

```
There seem to be a slew of options to the utility (try ./bar -h 2>&1 | less).

ok, so the code above spit out an error message, and i think I'm lost. Here is the script:```
#!/bin/bash
##This is a script to simply and easily copy DVDs to your hard drive from the command line
##For help send an email to wishingforayer@gmail.com	
############################################################################################################################################################
#####################################################		Variable Declaration		############################################################
############################################################################################################################################################
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}

MYHOME=/home/$USER
VIDEO=/home/$USER/video/dvds
############################################################################################################################################################
#####################################################		Scripted Action			############################################################
############################################################################################################################################################
        echo -e "Hello" $USER", How are you??"	
	echo -e "Where would you like the ISO created?"
           OPTIONS="Home User-Specified Video/dvd QUIT"
           select opt in $OPTIONS; do
               if [ "$opt" = "Home" ]; then                
                DIRECTORY=$MYHOME
               elif [ "$opt" = "User-Specified" ]; then
                echo -e "Please enter the directory into which you would like to create your ISO: " 
		read  DIRECTORY
	       elif [ "$opt" = "Video/dvd" ]; then
                 safemk video/dvds
		 DIRECTORY=$VIDEO
	       elif [ "$opt" = "QUIT" ]; then
		 exit 0
               else
                clear
                echo "That wasn't one of the options."
               fi
               break
           done
	echo -e "Please enter the desired filename for your ISO: " 
	read "FILENAME"
	dd if=/dev/cdrom | bar -s $EXPECTED_SIZE | dd of=$DIRECTORY/"$FILENAME".iso
	eject /dev/cdrom
	exit 0
```

and here is the error:```
brendon@brendon-linux:~/devbin$ ./cpdvdpb.sh 
Hello brendon, How are you??
Where would you like the ISO created?
1) Home
2) User-Specified
3) Video/dvd
4) QUIT
#? 1
Please enter the desired filename for your ISO: 
cod
*** ERROR: [2]: No such file or directory
           Missing size after -s
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.688e-05 seconds, 0.0 kB/s
brendon@brendon-linux:~/devbin$ 

```
Any Ideas??

---

### Post by frup on 2007-08-17
```
dd **if**=/dev/cdrom | bar -s **$EXPECTED_SIZE** | dd **of**=$DIRECTORY/"$FILENAME".iso
```

Your $EXPECTED_SIZE variable is empty no?

is that ment to be of? or if?

dd if=/
dd of=

---

### Post by cwaldbieser on 2007-08-17
You might try running your script with
```

$ bash -x <your script here>

```
That way, you can see what the interpreter is interpreting.

---

### Post by brennydoogles on 2007-08-17
> **cwaldbieser said:**
> You might try running your script with
```

$ bash -x <your script here>

```
That way, you can see what the interpreter is interpreting.

ok, so it is missing the size of the file for bar. Is there a way to have bash find the size of the DVD (Either 4.7GB or 7.4GB Usually) so that I can declare it to a variable??

---

### Post by cwaldbieser on 2007-08-17
> **brennydoogles said:**
> ok, so it is missing the size of the file for bar. Is there a way to have bash find the size of the DVD (Either 4.7GB or 7.4GB Usually) so that I can declare it to a variable??

Well, there are probably multiple ways.  If it is a data DVD, you could probably mount it and then use "du".  If you don't care about making two passes, you could pipe the dd output to "wc -c", but your users might end up waiting a significant amount of time just so you can compute the size of the DVD in that case.

---

### Post by brennydoogles on 2007-08-17
> **cwaldbieser said:**
> Well, there are probably multiple ways.  If it is a data DVD, you could probably mount it and then use "du".  If you don't care about making two passes, you could pipe the dd output to "wc -c", but your users might end up waiting a significant amount of time just so you can compute the size of the DVD in that case.

The use of this script is for making .iso backups of my dvd's to watch while away from home. With that said, the dvd automounts, and then I call the script. I would prefer not to make the copy take much longer if I can avoid it (I have the script working already without a progress bar, and if I have to choose between a progress bar and several minutes of extra copy time I will have to favor time), but I am willing to sacrifice some time to make the script more user friendly.

---

### Post by s1ightcrazed on 2007-08-17
```
du -ks /media/dvd | awk '{ print $1 }'
```

perhaps?

---

### Post by brennydoogles on 2007-08-18
> **s1ightcrazed said:**
> ```
du -ks /media/dvd | awk '{ print $1 }'
```

perhaps?

That is indeed the command I need. While attempting to integrate it into the script, I am running into an error message. I have attempted declaring the output of that command as a variable, but I am still new at redirecting and piping, so i am sure I have done it wrong. I also tried putting that whole command in parenthesis as the first argument to bar, but then I got an error with the dd command. I commented out my attempt to declare the variable, and here is the current state of the script: ```
#!/bin/bash
##This is a script to simply and easily copy DVDs to your hard drive from the command line
##For help send an email to wishingforayer@gmail.com	
############################################################################################################################################################
#####################################################		Variable Declaration		############################################################
############################################################################################################################################################
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}

MYHOME=/home/$USER
VIDEO=/home/$USER/video/dvds
#du -ks /media/cdrom0/ | awk '{ print $1 }' > $EXPECTED_SIZE
############################################################################################################################################################
#####################################################		Scripted Action			############################################################
############################################################################################################################################################
        echo -e "Hello" $USER", How are you??"	
	echo -e "Where would you like the ISO created?"
           OPTIONS="Home User-Specified Video/dvd QUIT"
           select opt in $OPTIONS; do
               if [ "$opt" = "Home" ]; then                
                DIRECTORY=$MYHOME
               elif [ "$opt" = "User-Specified" ]; then
                echo -e "Please enter the directory into which you would like to create your ISO: " 
		read  DIRECTORY
	       elif [ "$opt" = "Video/dvd" ]; then
                 safemk video/dvds
		 DIRECTORY=$VIDEO
	       elif [ "$opt" = "QUIT" ]; then
		 exit 0
               else
                clear
                echo "That wasn't one of the options."
               fi
               break
           done
	echo -e "Please enter the desired filename for your ISO: " 
	read "FILENAME"
	dd if=/dev/cdrom | bar -s (du -ks /media/cdrom0/ | awk '{ print $1 }') | dd of=$DIRECTORY/"$FILENAME".iso
	eject /dev/cdrom
	exit 0
```
and here is the error message: ```
brendon@brendon-linux:~/devbin$ ./cpdvdpb.sh 
Hello brendon, How are you??
Where would you like the ISO created?
1) Home
2) User-Specified
3) Video/dvd
4) QUIT
#? 1
Please enter the desired filename for your ISO: 
test
./cpdvdpb.sh: line 42: syntax error near unexpected token `('
./cpdvdpb.sh: line 42: `        dd if=/dev/cdrom | bar -s (du -ks /media/cdrom0/ | awk '{ print $1 }') | dd of=$DIRECTORY/"$FILENAME".iso'

```
Any Ideas??

---

### Post by brennydoogles on 2007-08-18
Progress!! I have succeeded in naming the variable with the correct size, and there is now a progress bar in the script. Unfortunately it does not seem set up correctly on the bar end. When copying the file, it has completed almost 400% within seconds!! So, I guess I need to figure out how to set the units in either bar or du. I will look at both man pages tomorrow, but if before then anyone has a good idea right off the top of their head I would love to hear it!! I will include the updated script here: ```
#!/bin/bash
##This is a script to simply and easily copy DVDs to your hard drive from the command line
##For help send an email to wishingforayer@gmail.com	
############################################################################################################################################################
#####################################################		Variable Declaration		############################################################
############################################################################################################################################################
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}

MYHOME=/home/$USER
VIDEO=/home/$USER/video/dvds
let EXPECTED_SIZE=$(du -ks /media/cdrom0/ | awk '{ print $1 }')
############################################################################################################################################################
#####################################################		Scripted Action			############################################################
############################################################################################################################################################
        echo -e "Hello" $USER", How are you??"	
	echo -e "Where would you like the ISO created?"
           OPTIONS="Home User-Specified Video/dvd QUIT"
           select opt in $OPTIONS; do
               if [ "$opt" = "Home" ]; then                
                DIRECTORY=$MYHOME
               elif [ "$opt" = "User-Specified" ]; then
                echo -e "Please enter the directory into which you would like to create your ISO: " 
		read  DIRECTORY
	       elif [ "$opt" = "Video/dvd" ]; then
                 safemk video/dvds
		 DIRECTORY=$VIDEO
	       elif [ "$opt" = "QUIT" ]; then
		 exit 0
               else
                clear
                echo "That wasn't one of the options."
               fi
               break
           done
	echo -e "Please enter the desired filename for your ISO: " 
	read "FILENAME"
	echo "expected size=" $EXPECTED_SIZE
        dd if=/dev/cdrom | bar -s $EXPECTED_SIZE | dd of=$DIRECTORY/"$FILENAME".iso
	eject /dev/cdrom
	exit 0
```

---

### Post by cwaldbieser on 2007-08-18
The bar program seems to accept common suffixes for size units.  For example:
```

$ dd if=/dev/zero bs=1024 count=1024000 | ./bar -s 1000m -nan > /dev/null

```
This pipeline copies 1024000 blocks of size 1024 zero-bytes to /dev/null.  The bar program is expecting a final size of 1000m or 1000*1024*1024 (1M = 1024*1024).  You can see the sizes are the same:
1000*1024*1024 == 1024 * 1024000

By default, it looks like bar uses bytes:
```

$ dd if=/dev/zero bs=1024 count=1024000 | ./bar -s 1048576000 -nan > /dev/null

```

The du command has commands for setting the output block size.  Common options are -m, -k, -b (for 1M, 1K, 1byte).  You pretty much just need to get your units to match.

---

### Post by brennydoogles on 2007-08-18
ok, so I changed a few options around, and the progress bar part seems to be working correctly. Unfortunately I am running into some I/O errors. Here's what I have:```
#!/bin/bash
##This is a script to simply and easily copy DVDs to your hard drive from the command line
##For help send an email to wishingforayer@gmail.com	
############################################################################################################################################################
#####################################################		Variable Declaration		############################################################
############################################################################################################################################################
safemk () {
if [ ! -d $1 ]; 
  then mkdir $1; 
  chmod +rw $1; 
fi
}

MYHOME=/home/$USER
VIDEO=/home/$USER/video/dvds
let EXPECTED_SIZE=$(du -bs /media/cdrom0/ | awk '{ print $1 }')
############################################################################################################################################################
#####################################################		Scripted Action			############################################################
############################################################################################################################################################
        echo -e "Hello" $USER", How are you??"	
	echo -e "Where would you like the ISO created?"
           OPTIONS="Home User-Specified Video/dvd QUIT"
           select opt in $OPTIONS; do
               if [ "$opt" = "Home" ]; then                
                DIRECTORY=$MYHOME
               elif [ "$opt" = "User-Specified" ]; then
                echo -e "Please enter the directory into which you would like to create your ISO: " 
		read  DIRECTORY
	       elif [ "$opt" = "Video/dvd" ]; then
                 safemk video/dvds
		 DIRECTORY=$VIDEO
	       elif [ "$opt" = "QUIT" ]; then
		 exit 0
               else
                clear
                echo "That wasn't one of the options."
               fi
               break
           done
	echo -e "Please enter the desired filename for your ISO: " 
	read "FILENAME"
	echo "expected size=" $EXPECTED_SIZE
        dd if=/dev/cdrom | bar -s $EXPECTED_SIZE | dd of=$DIRECTORY/"$FILENAME".iso
	eject /dev/cdrom
	exit 0
```

and the errors: ```
brendon@brendon-linux:~/devbin$ ./cpdvdpb.sh 
Hello brendon, How are you??
Where would you like the ISO created?
1) Home
2) User-Specified
3) Video/dvd
4) QUIT
#? 1
Please enter the desired filename for your ISO: 
cod
expected size= 670864632
dd: reading `/dev/cdrom': Input/output error [=                                                                                                             ]
3296+0 records in
3296+0 records out
   1.6MB at 1687552 bytes (1.7 MB) copied 117.7KB/s  eta:   1:32:31    0% [=                                           , 13.6979 seconds, 123 kB/s
                                                                  ]
Copied: 1687552B (1.6MB) (0% of expected input)
Time: 14 seconds
Throughput: 120539B (117.7KB/s)

3296+0 records in
3296+0 records out
1687552 bytes (1.7 MB) copied, 13.7207 seconds, 123 kB/s

```

Any Ideas?

---

### Post by cwaldbieser on 2007-08-19
> **brennydoogles said:**
> 
```
brendon@brendon-linux:~/devbin$ ./cpdvdpb.sh 
Hello brendon, How are you??
Where would you like the ISO created?
1) Home
2) User-Specified
3) Video/dvd
4) QUIT
#? 1
Please enter the desired filename for your ISO: 
cod
expected size= 670864632
dd: reading `/dev/cdrom': Input/output error [=                                                                                                             ]
3296+0 records in
3296+0 records out
   1.6MB at 1687552 bytes (1.7 MB) copied 117.7KB/s  eta:   1:32:31    0% [=                                           , 13.6979 seconds, 123 kB/s
                                                                  ]
Copied: 1687552B (1.6MB) (0% of expected input)
Time: 14 seconds
Throughput: 120539B (117.7KB/s)

3296+0 records in
3296+0 records out
1687552 bytes (1.7 MB) copied, 13.7207 seconds, 123 kB/s

```

Any Ideas?

Well, I guess the first thing to try is to run the script with "bash -x" again and get the exact pipeline that your script is running to create the ISO image.  If you run that pipeline directly from the command line and it produces the same error, it could be that there are some errors on the CD.

You could try adding some options to your dd command:
```

dd if=/dev/cdrom **conv=notrunc,noerror,sync** | bar -s $EXPECTED_SIZE | dd of=$DIRECTORY/"$FILENAME".iso

```

The following link has some information that might be useful:
[http://www.troubleshooters.com/linux/coasterless.htm#_Accurately_Reading_a_CD]("http://www.troubleshooters.com/linux/coasterless.htm#_Accurately_Reading_a_CD")

I am by no means a CD/DVD expert, but from what I have picked up from doing some modest googling, if the optical media has been written as TAO (track at once) rather than DAO (disk at once), then there may be some extra issues.

---

### Post by brennydoogles on 2007-08-19
> **cwaldbieser said:**
> Well, I guess the first thing to try is to run the script with "bash -x" again and get the exact pipeline that your script is running to create the ISO image.  If you run that pipeline directly from the command line and it produces the same error, it could be that there are some errors on the CD.

You could try adding some options to your dd command:
```

dd if=/dev/cdrom **conv=notrunc,noerror,sync** | bar -s $EXPECTED_SIZE | dd of=$DIRECTORY/"$FILENAME".iso

```

The following link has some information that might be useful:
[http://www.troubleshooters.com/linux/coasterless.htm#_Accurately_Reading_a_CD]("http://www.troubleshooters.com/linux/coasterless.htm#_Accurately_Reading_a_CD")

I am by no means a CD/DVD expert, but from what I have picked up from doing some modest googling, if the optical media has been written as TAO (track at once) rather than DAO (disk at once), then there may be some extra issues.

Well, I am getting the same error with several cd's and Dvd's (retail dvd's that I was able to successfully backup before editing the script) and I think the problem is with piping the output of bar to the input of dd of=  . Here is the error: ```
brendon@brendon-linux:~/devbin$ bash -x cpdvdpb.sh
+ MYHOME=/home/brendon
+ VIDEO=/home/brendon/video/dvds
++ du -bs /media/cdrom0/
++ awk '{ print $1 }'
+ let EXPECTED_SIZE=4603760640
+ echo -e Hello 'brendon, How are you??'
Hello brendon, How are you??
+ echo -e 'Where would you like the ISO created?'
Where would you like the ISO created?
+ OPTIONS='Home User-Specified Video/dvd QUIT'
+ select opt in '$OPTIONS'
1) Home
2) User-Specified
3) Video/dvd
4) QUIT
#? 1
+ '[' Home = Home ']'
+ DIRECTORY=/home/brendon
+ break
+ echo -e 'Please enter the desired filename for your ISO: '
Please enter the desired filename for your ISO: 
+ read FILENAME
test
+ echo 'expected size=' 4603760640
expected size= 4603760640
+ dd if=/dev/cdrom
+ bar -s 4603760640
+ dd of=/home/brendon/test.iso
dd: reading `/dev/cdrom': Input/output error
   1.5MB at    0.0B/s   eta:3040+0 records in
3040+0 records out
1556480 bytes (1.6 MB) copied , 0.0395581 seconds, 39.3 MB/s
  0:00:00    0% [=                                                                                                             ]
Copied: 1556480B (1.5MB) (0% of expected input)
Time:  0 seconds
Throughput: (infinite)

3038+4 records in
3040+0 records out
1556480 bytes (1.6 MB) copied, 0.0622131 seconds, 25.0 MB/s
+ exit 0
brendon@brendon-linux:~/devbin$ 

```

I attempted to separate the bar and dd of= with a semicolon instead of a pipe, but I was completely unsuccessful in that regard. Any suggestions?

---

### Post by cwaldbieser on 2007-08-19
> **brennydoogles said:**
> Well, I am getting the same error with several cd's and Dvd's (retail dvd's that I was able to successfully backup before editing the script) and I think the problem is with piping the output of bar to the input of dd of=  . 

Try just redirecting the output of bar to the destination file, maybe?
```

dd if=/dev/cdrom | bar -s $EXPECTED_SIZE > $DIRECTORY/"$FILENAME".iso

```
The error still looks like it is happening during, the read, though.

What happens if you just type
```

$ dd if=/dev/cdrom | bar -s 4603760640

```
at the command prompt?  Same error?

---

### Post by brennydoogles on 2007-09-06
Ok, so it appears that the problem occurred because of some kind of error from the drive itself. After a fresh install of Ubuntu (not because of this, but actually because of a need to resize and move ALL of my partitions) everything works great. Now for one last question.... what would I have to do to create a deb for my script that would include the installation of bar and all required codecs, as well as putting the script in a place where it can be run from terminal or a quick launch Icon?

---

