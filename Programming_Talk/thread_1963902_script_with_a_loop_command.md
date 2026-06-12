---
title: "script with a loop command"
date: 2012-04-23
forum: Programming Talk
---

### Post by al090187 on 2012-04-23
Hi,

I am trying to create a script to run several Gaussian calculations in series, then email me the results file.

The Gaussian input files are each in a numerical folder, starting from 1 up to 17. 

After searching on the web, I came up with the following script which I assumed would work.

```
#!/bin/bash
for i in {1..17}
do
	if [ ! -f "/home/al/Desktop/Luis/$i/Input.log" ];
	then 	
		g03 /home/al/Desktop/Luis/$i/Input.com
		echo "Task $i done" | mutt -s "Task $i complete" My_Email_Address -a /home/al/Desktop/Luis/$i/Input.log
	fi
done
```

However, this just comes up with an error in finding a folder "/home/al/Desktop/Luis/{1..17}/Input.log"

Any suggestions as to why the {1..17} command isn't working? The script works fine if I use a list of numbers of the folders, just the range bit isn't working.


As an extension of this, I would like to be able to add further folders with further input files. Is there a way of making the script check for the highest folder number, and keep going until all files have been run? Or, even better, Can I specify the first and last values of the loop as variables prior to running the script, then let the script run and do its thing?

Thanks in advance for any help.

---

### Post by km3952 on 2012-04-23
Just offering this as no one else has chipped in...

Not sure, I'm not an expert, but 
> if [ ! -f "/home/al/Desktop/Luis/$i/Input.log" ];
doesn't look right to me; I think I would give it a try without the quotes & see if that works,
or perhaps try escaping the $ (ie \$i).

---

### Post by matt_symes on 2012-04-23
Hi

It's working on my machine, in that bash is substituting the correct value for n$i in the path.

```
matthew@matthew-Aspire-7540:~$./test
<snip>
Can't stat /home/al/Desktop/Luis/**15**/Input.log: No such file or directory
/home/al/Desktop/Luis/**15**/Input.log: unable to attach file.
./test: line 6: g03: command not found
Can't stat /home/al/Desktop/Luis/**16**/Input.log: No such file or directory
/home/al/Desktop/Luis/**16**/Input.log: unable to attach file.
./test: line 6: g03: command not found
Can't stat /home/al/Desktop/Luis/**17**/Input.log: No such file or directory
/home/al/Desktop/Luis/**17**/Input.log: unable to attach file.
matthew@matthew-Aspire-7540:~$
```

Can you copy and paste the exact output from the terminal into your next post.

Kind regards

---

### Post by al090187 on 2012-04-23
Thanks for the reply. The rest of the commands all work fine when the loop command is changed to 

```

for i in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17

```

So it is just when using the range command that doesn't work. The site here [http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/) is where I got the range details from, but they don't seem to work on my version.

Any further ideas?

---

### Post by mörgæs on 2012-04-23
Moved to Programming Talk.

---

### Post by al090187 on 2012-04-23
The exact output I get is below.

```
Segmentation fault
 Unable to open input file "/home/al/Desktop/Luis/{1..17}/Input.com".
Segmentation fault
Can't stat /home/al/Desktop/Luis/{1..17}/Input.log: No such file or directory
/home/al/Desktop/Luis/{1..17}/Input.log: unable to attach file.
```

---

### Post by matt_symes on 2012-04-23
Hi

What version of bash are you using ? Post back here.

```
bash --version
```

Kind regards

---

### Post by al090187 on 2012-04-23
Version is...

```
GNU bash, version 4.2.8(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

```

Thanks

---

### Post by matt_symes on 2012-04-23
Hi

According to that article, your version is bash is new enough to handle ranges.

Copy and paste this into a terminal.

```
for test in {1..20}; do echo /home/matthew/$test/tmp; done
```What output do you get ? You should get this
```

matthew@matthew-Aspire-7540:~$ for test in {1..20}; do echo /home/matthew/$test/tmp; done
/home/matthew/1/tmp
/home/matthew/2/tmp
/home/matthew/3/tmp
/home/matthew/4/tmp
/home/matthew/5/tmp
/home/matthew/6/tmp
/home/matthew/7/tmp
/home/matthew/8/tmp
/home/matthew/9/tmp
/home/matthew/10/tmp
/home/matthew/11/tmp
/home/matthew/12/tmp
/home/matthew/13/tmp
/home/matthew/14/tmp
/home/matthew/15/tmp
/home/matthew/16/tmp
/home/matthew/17/tmp
/home/matthew/18/tmp
/home/matthew/19/tmp
/home/matthew/20/tmp
matthew@matthew-Aspire-7540:~$ 
```Kind regards

---

### Post by al090187 on 2012-04-23
Yes, I do get that result. It just doesn't seem to work in the script. 

Could it be anything to do with the way I start the script? I just tried starting it using "nohup ./queue.sh" and it seems to have worked OK, whereas before I was using "nohup sh ./queue.sh".

Thanks.

---

### Post by matt_symes on 2012-04-23
Hi

> **al090187 said:**
> Could it be anything to do with the way I start the script? I just tried starting it using "nohup ./queue.sh" and it seems to have worked OK, whereas before I was using "nohup [COLOR=Red]**_sh_**[/COLOR] ./queue.sh".

That is your problem. You are running it under sh and not bash that way.

```
nohup bash ./queue.sh
```That will work and so will

```
nohup ./queue.sh
```They will both use the Bash shell and not sh. 

The first specifies the shell to use on the command line; the second will use the shell specified in the script (in your case #!/bin/bash)

What you are doing when running this command (nohup [COLOR=Red]**_sh_**[/COLOR] ./queue.sh) is to override the shell it is using (to use sh) and sh does not have ranges, only bash.

Kind regards

---

### Post by al090187 on 2012-04-23
Ah hah. Problem solved. Thank you very much!

Do you have any advice on the specifying range as variables before running the script? 

Changing the loop to
```
for i in {$bottom..$top}
```
seems to give the right input to the script, as the error comes up the same as before, but even using the right command for the script, it doesn't work.
```
al-grs:~$ export top="19" bottom="18"
al-grs:~$ ./queue.sh
 Unable to open input file "/home/al/Desktop/Luis/{18..19}/Input.com".
./queue.sh: line 2:  9438 Segmentation fault      g03 /home/al/Desktop/Luis/$i/Input.com
Can't stat /home/al/Desktop/Luis/{18..19}/Input.log: No such file or directory
/home/al/Desktop/Luis/{18..19}/Input.log: unable to attach file.

```

The variables appear to be recognised, but the range now does not work again. Do I have to define the variables in a different way for bash scripts to work still?

---

### Post by matt_symes on 2012-04-23
Hi

Here is a modified script.

```

#!/bin/bash

for (( i=$bottom; i <= $top; i++ ))
do
        if [ ! -f "/home/al/Desktop/Luis/$i/Input.log" ];
        then    
                g03 /home/al/Desktop/Luis/$i/Input.com
                echo "Task $i done" | mutt -s "Task $i complete" My_Email_Address -a /home/al/Desktop/Luis/$i/Input.log
        fi
done
```You can call it like this.

```
bottom=1 top=10 ./queue.sh
```Have you considered screen instead of nohup ? Much more flexable.

Kind regards

---

### Post by al090187 on 2012-04-23
Awesome. That script is amazing. Thank you!


I haven't considered screen, no. What kind of advantages would it give me? I just submit the script and leave it. Then get the emails to tell me each individual task has completed.

---

### Post by matt_symes on 2012-04-23
Hi

> **al090187 said:**
> Awesome. That script is amazing. Thank you!

I'm glad you like it. It was only a small mod, so kudos to the original script writer.

> I haven't considered screen, no. What kind of advantages would it give me? I just submit the script and leave it. Then get the emails to tell me each individual task has completed.screen allows you to have multiple bash sessions open at the same time running under screen. Here is a quick tutorial.

[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

The best part is attach and detach. You can detach from the screen session and it will keep on running along with any scripts running on it. Later you can reattach to the screen session and all the scripts you had running will still be running (or finished if they have finished)

It's great for servers over ssh, to run scripts after the ssh session has closed.

Why were you using nohup in the first place ?

Kind regards

---

### Post by al090187 on 2012-04-23
I created the script with help from various websites, and a little intuition. It's my first attempt at any kind of meaningful script for my own uses, so just needed that little bit of knowledge in the area. Before I have just copied other scripts and changed file names etc.

I was using nohup to access a server over ssh. Kept wondering why the script kept getting stopped until I realised how to use this.

Screen does sound useful, however not so much in this case. There are no outputs to the command line at all once the calculation starts. Once I submit the queue file with the all important &, everything goes to the output file, and I can close the ssh session and forget about it. 

I shall almost definitely use screen in the future though. Thanks again for your help.

---

