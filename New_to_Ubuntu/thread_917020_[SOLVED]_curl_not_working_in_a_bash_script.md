---
title: "[SOLVED] curl not working in a bash script"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Cheesehead on 2008-09-11
=== Solved - see the solution at the bottom of the first post (this one) ===

The following executes beautifully on the command line:

```
ian@apathy:~$ curl http://www.whatismyip.com/automation/n09230945.asp
xxx.xxx.xxx.xxxian@apathy:~$ 
```


But in the following script, it fails...looking for ideas on how to fix it!

Script:
```
#!/bin/sh
external_ip=curl http://www.whatismyip.com/automation/n09230945.asp
echo "My IP address is: "$external_ip
echo "End!"
```

Output:
```
ian@apathy:~$ ./curl_test.sh 
./curl_test.sh: 2: http://www.whatismyip.com/automation/n09230945.asp: not found
My IP address is: 
End!
ian@apathy:~$ 
```


=== SOLUTION ===

I needed to put the curl command in quotes...the right *kind* of quotes (slanted quotes found on the tilde '~' key on a US keyboard.

The final script that works great is:
```
#!/bin/sh
external_ip=`curl http://www.whatismyip.com/automation/n09230945.asp`
echo "My IP address is: "$external_ip
echo "End!"
```

Thanks to everyone for their help...

---

### Post by whitethorn on 2008-09-11
Well I'm not really sure why it doesn't work.  But I got it to work.  Only problem is it's not all in one line.

```

#!/bin/sh
$external_ip
echo "My external IP address is"; curl http://www.whatismyip.com/automation/n09230945.asp; echo " End!"

```

---

### Post by jamesrl on 2008-09-11
```
#!/bin/sh
external_ip=`curl http://www.whatismyip.com/automation/n09230945.asp`
echo "My IP address is: "$external_ip
echo "End!"

```
works for me by adding the ` ` quotes around the command.
Also note, this is a sh shell script (hence the #!/bin/sh as opposed to #!/bin/bash for a bash script).

---

### Post by jamesrl on 2008-09-11
Also in general when debugging a sh/bash script, it helps to display output from the file.
So run 
```
bash -xv temp.sh
```
-v is for 'verbose' (write the each line of the script to standard error before it is run), and 
-x is for writing each command that gets executed to standard error.

So for your original script you get:
```
#!/bin/sh
external_ip=curl http://www.whatismyip.com/automation/n09230945.asp
+ external_ip=curl
+ http://www.whatismyip.com/automation/n09230945.asp
temp.sh: line 2: http://www.whatismyip.com/automation/n09230945.asp: No such file or directory
echo "My IP address is: "$external_ip
+ echo 'My IP address is: '
My IP address is: 
echo "End!"
+ echo 'End!'
End!
```

So you can immediately see the problem, bash ran the command curl with no arguments, set the output to external_ip, and then tried running [http://www.whatismyip.com/automation/n09230945.asp](http://www.whatismyip.com/automation/n09230945.asp) as a seperate command.

For more help [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/"), though for all but the simplest scripts, I would strong recommend trying python for your scripts.

---

### Post by Cheesehead on 2008-09-11
1) Okay, so it's a *dash* script. Got it. Is there an important difference?

2) I need to save the IP address as a variable - that's the point of the test. I plan to use it later.

3) Suggested single-quotes works great, but still doesn't give me what I want:
Script:
```
#!/bin/sh
external_ip='curl http://www.whatismyip.com/automation/n09230945.asp'
echo "My IP address is: "$external_ip
echo "End!"
```

Output:
```
ian@apathy:~$ ./curl_test.sh 
My IP address is: curl http://www.whatismyip.com/automation/n09230945.asp
End!
ian@apathy:~$ 

```

---

### Post by whitethorn on 2008-09-11
You're using the wrong kind of quotes.  There is '  and `   which is on the tilda button.

---

### Post by jamesrl on 2008-09-11
Pay attention to the type of quote.  For me I need the tilted single quote.  On my keyboard its on the same key as tilde.  The backquote ` not ' or ", all of which have differences.

---

### Post by jamesrl on 2008-09-11
Basically the difference between the quotes can be seen by defining a variable and echoing.

Define your variable in the shell as:
```

export MY_VAR="ls -l"

```

Then type
```

export doubquotes="$MY_VAR"
echo $doubquotes
export singquotes='$MY_VAR'
echo $singquotes
export backquotes=`$MY_VAR`
echo $backquotes

```
the double quotes replaces the variable with its contents; the single quotes prints out the variable name; and the backquotes executes the command.

---

### Post by jamesrl on 2008-09-11
> **Cheesehead said:**
> 1) Okay, so it's a *dash* script. Got it. Is there an important difference?

In general bash has a little more features than sh/dash, and slightly different syntax.  For a quick example, try
```

echo "\\n"

```
in both bash and sh.  These small difference cause problems, when people specify /bin/sh but expect to use bash features.  See:
[https://wiki.ubuntu.com/DashAsBinSh]("https://wiki.ubuntu.com/DashAsBinSh")

---

