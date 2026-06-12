---
title: "Pipe Terminal Output to Zenity"
date: 2007-12-19
forum: Programming Talk
---

### Post by altonbr on 2007-12-19
I'm trying to run this and pipe it to Zenity...
```
aptitude install zenity | zenity --text-info
```
Of course that doesn't work because it doesn't use 'sudo' and just hangs.

How do I get Zenity to ask for a password and then pipe it to sudo?
This asks via the command-line the password, but not in Zenity:
```
sudo aptitude install zenity | zenity --text-info
```

I know I need 'zenity --entry' to ask the user for some input, but once I received that information, how do I feed 'sudo' that password? Or am I going about this the wrong way?

---

### Post by altonbr on 2007-12-19
Got it.
```
PASSWORD=`zenity --title='Password' --text='Please enter your password' --entry`
echo $PASSWORD | sudo -S aptitude install zenity | zenity --text-info
```

---

### Post by aJayRoo on 2007-12-19
I think it would be more secure to simply use gksudo to run the command and pipe the output to zenity:
```
gksudo command_that_needs_sudo | zenity_stuff
```
That way a graphical password prompt will be shown and there is no need to handle the password yourself in plain text.

---

### Post by altonbr on 2007-12-19
This is how Automatix does it:
```
gksudo --message "Please enter your admin password to start Automatix" "/usr/bin/automatix.py $USER $HOME $UID $1"
```

---

### Post by altonbr on 2007-12-26
The problem with this:
```
while [ -z $PASSWORD ]; do
	echo $LEVELINFO "Asking user for their password..."
	PASSWORD=`zenity --title='Password' --text='Please enter your password' --entry`
done

export PASSWORD
```

Is that (1) You've just accepted a 'sudo' password in open text and (2) now you've exported the open password!

How can I use 'sudo's "register the password for 5 minutes" feature but make it graphical by using zenity AND not run a shell program like my Automatix example?

---

### Post by sundar_ima on 2011-04-16
I know it is ver old thread but i think this is the correct place to clear my doubt. The code given below works with out an issue. ```
PASSWORD=`zenity --title='Password' --text='Please enter your password' --entry`
echo $PASSWORD | sudo -S aptitude install zenity | zenity --text-info
```
My question is that how do you close the text info box once the operation is complete?

---

### Post by hakermania on 2011-04-16
please mark the thread as solved

---

