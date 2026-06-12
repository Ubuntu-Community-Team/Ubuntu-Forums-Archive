---
title: "Login script"
date: 2011-07-31
forum: Programming Talk
---

### Post by Majere79 on 2011-07-31
I would like to use a shell script to login to Cisco IOS devices.  I have searched for, found, and tried several different things but nothing had worked out.  This may be due to me being a complete novice when it comes to shell scripting.

Specifically, I want the script to log the user in, and then the user can interact with the IOS command line once the script is done with the login.

I am not sure if I should post the code, but I will if that is helpful.

---

### Post by Arndt on 2011-07-31
> **Majere79 said:**
> I would like to use a shell script to login to Cisco IOS devices.  I have searched for, found, and tried several different things but nothing had worked out.  This may be due to me being a complete novice when it comes to shell scripting.

Specifically, I want the script to log the user in, and then the user can interact with the IOS command line once the script is done with the login.

I am not sure if I should post the code, but I will if that is helpful.

Either post the code (best in a reduced form that still exhibits the problem, if you can), or describe in more details what the problems are.

---

### Post by Majere79 on 2011-07-31
clear
echo "Connecting to 192.168.1.1"
ssh tsmith@192.168.1.1
expect "password:"
send -- "test123\r"

I get the ssh password prompt but then nothing happens.

---

### Post by fdrake on 2011-07-31
> **Majere79 said:**
> clear
echo "Connecting to 192.168.1.1"
ssh tsmith@192.168.1.1
expect "password:"
send -- "test123\r"

I get the ssh password prompt but then nothing happens.

did you try 
```

pass="test123\r"
ssh tsmith@192.168.1.1 < $pass 
```?

more [help in here]("http://nixcraft.com/shell-scripting/4489-ssh-passing-unix-login-passwords-through-shell-scripts.html")

---

### Post by Majere79 on 2011-07-31
Just tried it...and I get:

./testlogin.sh: line 4: test123\r: No such file or directory

---

### Post by fdrake on 2011-07-31
```

cat > login.txt 
192.168.1.1|tsmith|test123\r

```
```

cat > sshlogin.sh
#!/bin/bash
FILE=login.txt
CONNECT=sshlogin.exp
SERVERNAME=$1
MyServer=""
MyUser=""
MyPassword=""
exec 3<&0
exec 0<$FILE
while read line
do
        MyServer=$(echo $line | cut -d'|' -f1)
        MyUser=$(echo $line | cut -d'|' -f2)
        MyPassword=$(echo $line | cut -d'|' -f3)
        if [ "$SERVERNAME" == "$MyServer" ];
        then
           echo "Running ssh $MyUser@$MyServer..."
          $CONNECT $MyPassword $MyServer $MyUser
        fi
done
exec 0<&3
echo "$SERVERNAME not found in login.txt file"

```
```
sudo chomod +x sshlogin.sh
./sshlogin.sh
```

check the link on my prev post

---

### Post by Majere79 on 2011-07-31
Any way to avoid storing the login credentials in a file?

---

### Post by fdrake on 2011-07-31
> **Majere79 said:**
> Any way to avoid storing the login credentials in a file?

so you want to save the info in the script ?(which is the same as saving it on a file) or do you want the script to ask you for the info?

---

### Post by Majere79 on 2011-07-31
The credentials will be pulled from a database once the user selects a device.  I was hoping to store the password in a variable and then pass it to the login.

---

### Post by Arndt on 2011-07-31
> **Majere79 said:**
> clear
echo "Connecting to 192.168.1.1"
ssh tsmith@192.168.1.1
expect "password:"
send -- "test123\r"

I get the ssh password prompt but then nothing happens.

'expect' and 'send' are not Linux commands that I know, but they are used as commands in the 'expect' program, and you should probably write the whole script for use with 'expect'.

If this is a shell script, it's natural that it stops at the password prompt: first ssh is called, and it wants a password. When ssh has completed, that is, when you have logged out, bash will continue with what's after the ssh call.

---

### Post by Majere79 on 2011-07-31
So, in other words, what I want to do won't work?  What is meant when you say "you should probably write the whole script for use with 'expect'."

---

### Post by Arndt on 2011-07-31
> **Majere79 said:**
> So, in other words, what I want to do won't work?  What is meant when you say "you should probably write the whole script for use with 'expect'."

I wrote my post when I hadn't read the others yet. The solution by fdrake does use 'expect', in the sshlogin.exp script, so I have nothing material to contribute - you should try to get his solution to work.

---

### Post by Majere79 on 2011-08-02
Ok, I figured out how to SSH to a device.  Thanks to all for the help.  Now, I am looking to display a list of items, highlight the item and be able to take action on the selected item (i.e call the SSH script).  I have no idea where to start on this part of it!

---

### Post by fdrake on 2011-08-02
> **Majere79 said:**
> Ok, I figured out how to SSH to a device.  Thanks to all for the help.  Now, I am looking to display a list of items, highlight the item and be able to take action on the selected item (i.e call the SSH script).  I have no idea where to start on this part of it!
can u be alit bit more detailed?
what kind of list? file list?
what do u mean by highlighting? selecting the item?
give us an example.

---

### Post by Majere79 on 2011-08-02
So, the program presents you with a list of devices, you can then use the up and down arrows to highlight a device and then press enter to connect to that device.  

How do I generate a "live" list where you can select a single line item using the keyboard?  In other words, I would like to get a script to respond to arrow key presses to scroll up and down a menu.

---

### Post by Majere79 on 2011-09-06
Alright, thanks for everyone's advice!  I have been slowly refreshing my knowledge of C programming and have been able to generate a usable GUI that will allow the user to select from a list of items.  The problem I am facing now is related to array programming.

So, the code returns an array from SQL query which represents the information and the menu function uses an array to display the choices.  It seems to me that I need to somehow show and array of arrays to display multiple rows of information in the menu.  I definitely could use some advice on this or maybe even a recommendation on a better way to display the information.

---

