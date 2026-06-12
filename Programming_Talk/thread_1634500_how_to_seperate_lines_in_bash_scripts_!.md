---
title: "how to seperate lines in bash scripts !"
date: 2010-11-30
forum: Programming Talk
---

### Post by slashwannabe94 on 2010-11-30
Hello all, 

i have decided to male a bash script to install and correctly append my  gmail settings to the /etc/ssmtp/ssmtp.conf file. but i do not know who  to seperate lines of code when scripting. 

here is my code... i know its crap but im a n00b to coding haha XD

#!/bin/bash 

sudo -i

echo "Welcome to sTaTiC's gmail setup..."

echo "Installing SSMTP..."

sudo apt-get install ssmtp

echo "SSMTP installation complete!"

sleep 2

echo "Installing heirloom-mailx..."

sudo apt-get install heirloom-mailx

echo "heirloom-mailx installation complete!"

sleep 2

echo "configuring ssmtp.conf..."

rm /etc/ssmtp/ssmtp.conf 

echo AuthUser=myemail@googlemail.com ; AuthPass=password ;  FromLineOverride=YES ; mailhub=smtp.gmail.com:587 ; UseSTARTTLS=YES  >> /etc/ssmtp/ssmtp.conf

how do append the configuration settings, to the /etc/ssmtp/ssmtp.conf file so it looks like this when opened in a text editor?

AuthUser=email@googlemail.com
AuthPass=password
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES

please help

---

### Post by diesch on 2010-11-30
Use  a  *here-document*
```
cat<<EOF  >>/etc/ssmtp/ssmtp.conf
AuthUser=email@googlemail.com
AuthPass=password
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
EOF
```

---

### Post by surfer on 2010-11-30
what about this? you do not have to remove the file first; ">" will purge the file if it exists.
```

echo "AuthUser=myemail@googlemail.com" > /etc/ssmtp/ssmtp.conf
echo "AuthPass=password"               >> /etc/ssmtp/ssmtp.conf
echo "FromLineOverride=YES"            >> /etc/ssmtp/ssmtp.conf
...etc
```

---

### Post by surfer on 2010-11-30
> **diesch said:**
> Use  a  *here-document*
```
cat<<EOF  >>/etc/ssmtp/ssmtp.conf
AuthUser=email@googlemail.com
AuthPass=password
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
EOF
```

ok, that is nicer indeed!

---

### Post by DaithiF on 2010-11-30
cat <<EOF >> /etc/ssmtp/ssmtp.conf
AuthUser=myemail@googlemail.com 
AuthPass=password 
FromLineOverride=YES 
mailhub=smtp.gmail.com:587 
UseSTARTTLS=YES 
EOF

---

### Post by slashwannabe94 on 2010-11-30
thank you guys, 

could one of you explain to me, what <<EOF>> is and does ?

---

### Post by paulsarmiento on 2010-12-01
hi slashwannabe94,

The ">>" are append redirection switches in bash and "<<" is also a redirection switch for accept input. the EOF is the switch for bash to indicate a sequence of information and will be terminated by an EOF.

If you really like to get into bash scripting, there are so many available resources out there.

Paul

---

### Post by DaithiF on 2010-12-01
EOF is just an arbitrary string which acts as a termination marker -- it could be any text, e.g., <<end_of_section would work too.  (Though its a fairly common convention to use EOF as the choice of marker)

For more on here documents, the bash man page says it best:
```
man bash | less +/"Here Document"

```

---

### Post by slashwannabe94 on 2010-12-08
Hello, i have changed the script to look like this.. but i have no luck in making it work. i want each line of quoted code to be added to the /etc/ssmtp/ssmtp.conf file. but when i run the script, it just overwrites the first line and gives me the output 

STARTTLS=YES

i want the contents of /etc/ssmtp/ssmtp.conf to look like this...

AuthUser=myemail@googlemail.com
 AuthPass=password 
FromLineOverride=YES
 mailhub=smtp.gmail.com:587
 STARTTLS=YES


CODE 

#!/bin/bash 

echo "AuthUser=myemail@googlemail.com" > /etc/ssmtp/ssmtp.conf

echo "AuthPass=password" > /etc/ssmtp/ssmtp.conf 

echo "FromLineOverride=YES" > /etc/ssmtp/ssmtp.conf

echo "mailhub=smtp.gmail.com:587" > /etc/ssmtp/ssmtp.conf

echo "STARTTLS=YES" > /etc/ssmtp/ssmtp.conf

exit

---

### Post by msandoy on 2010-12-08
You need to use the append operator.
```

#!/bin/bash

echo "AuthUser=myemail@googlemail.com" > /etc/ssmtp/ssmtp.conf
echo "AuthPass=password" >> /etc/ssmtp/ssmtp.conf
echo "FromLineOverride=YES" >> /etc/ssmtp/ssmtp.conf
echo "mailhub=smtp.gmail.com:587" >> /etc/ssmtp/ssmtp.conf
echo "STARTTLS=YES" >> /etc/ssmtp/ssmtp.conf
exit

```
Like this.
">" will overwrite the file, and ">>" will append to an existing file.

---

### Post by slashwannabe94 on 2010-12-08
#!/bin/bash 

echo "AuthUser=myemail@googlemail.com" > /etc/ssmtp/ssmtp.conf
       
echo "AuthPass=password" >> /etc/ssmtp/ssmtp.conf 
      
echo "FromLineOverride=YES" >> /etc/ssmtp/ssmtp.conf
      
echo "mailhub=smtp.gmail.com:587" >> /etc/ssmtp/ssmtp.conf
      
echo "STARTTLS=YES" >> /etc/ssmtp/ssmtp.conf

exit

i have changed it to this and all i get in the /etc/ssmtp/ssmtp.conf file is AuthPass=Password

why is it not appending the other codes ?

---

### Post by slashwannabe94 on 2010-12-08
The command 

cat /home/marcom/reference.txt >> /etc/ssmtp/ssmtp.conf

works fine and takes the input from the file reference.txt file and places it /etc/ssmtp/ssmto.conf file. DONE!

But when i add this line of code to a script nothing happens.... ? 

cat /home/marcom/reference.txt >> /etc/ssmtp/ssmtp.conf

---

### Post by DaithiF on 2010-12-09
> **slashwannabe94 said:**
> Hello, i have changed the script to look like this.. but i have no luck in making it work. i want each line of quoted code to be added to the /etc/ssmtp/ssmtp.conf file. but when i run the script, it just overwrites the first line and gives me the output 

STARTTLS=YES

i want the contents of /etc/ssmtp/ssmtp.conf to look like this...

AuthUser=myemail@googlemail.com
 AuthPass=password 
FromLineOverride=YES
 mailhub=smtp.gmail.com:587
 STARTTLS=YES


CODE 

#!/bin/bash 

echo "AuthUser=myemail@googlemail.com" > /etc/ssmtp/ssmtp.conf

echo "AuthPass=password" > /etc/ssmtp/ssmtp.conf 

echo "FromLineOverride=YES" > /etc/ssmtp/ssmtp.conf

echo "mailhub=smtp.gmail.com:587" > /etc/ssmtp/ssmtp.conf

echo "STARTTLS=YES" > /etc/ssmtp/ssmtp.conf

exit

this doesn't look anything like the solution diesch or I suggested.  why didn't you try one of those?

---

### Post by slashwannabe94 on 2010-12-09
Hello, 

i tried the code below with no luck... i have even run the program as root and tried adding sudo -i to the beginning of the script..... IM TEARING MY HAIR OUT OVER THIS! 
please help people, you are my last hope :)  

#!/bin/bash

cat <<EOF >> /etc/ssmtp/ssmtp.conf
AuthUser=myemail@googlemail.com
AuthPass=password
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
EOF

exit

---

### Post by DaithiF on 2010-12-09
does your user have permissions to write to /etc/ssmtp/ssmtp.conf ?

if yes, then just run the script, it will work.

if not, then run the script with sudo.

sudo path/to/script

thats all

---

### Post by diesch on 2010-12-09
Adding *sudo -i *doesn't help as this will run an interactive root shell but will not run the following shell code as root.

To have the script automatically run with sudo use
```

if [ "$(/usr/bin/id -u)" != "0" ]; then
   exec /usr/bin/sudo "$0"
fi

```
at the beginning. This checks if the script is already running as root and restarts it using sudo if it's not.

---

### Post by slashwannabe94 on 2010-12-10
thank you so much guys :D :D :D 

THAT WORKED!!!!

My finished code :~)

if you guys can think of anything to make this script any better, then please post. :D :D :D 
-----------------------------------------------------------

#!/bin/bash

if [ "$(/usr/bin/id -u)" != "0" ]; then
   exec /usr/bin/sudo "$0"
fi

echo "Welcome to sTaTiC's gmail setup..."

echo "Installing SSMTP..."

sudo apt-get install ssmtp

echo "SSMTP installation complete!"

sleep 2

echo "Installing heirloom-mailx..."

sudo apt-get install heirloom-mailx

echo "heirloom-mailx installation complete!"

echo "configuring ssmtp.conf..."

rm /etc/ssmtp/ssmtp.conf

cat <<EOF >> /etc/ssmtp/ssmtp.conf
AuthUser=static1001@googlemail.com
AuthPass=linustorvalds
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
EOF

sleep 2 

echo "Done!"

exit
----------------------------------------------------------

Thanks guys you saved my *** :P

---

### Post by DaithiF on 2010-12-10
> **slashwannabe94 said:**
> 
if you guys can think of anything to make this script any better, then please post. 

1. check the exit code from each external command and exit if non-zero (non-zero indicating a failure), to prevent your script blindly carrying on despite a failure along the way.

after each step:
```
[[ $? -eq 0 ]] || { echo "Failed to do XXX, exiting...; exit 1; }

```

2. if a configuration file already exists it would be polite to take a backup copy of it before overwriting it
```
[[ -e /etc/ssmtp/ssmtp.conf ]] && cp /etc/ssmtp/ssmtp{.conf,.bak}

```

3. you **rm **the config file and then **append **content to it.  although it will work it doesn't make sense.  don't bother with the rm, just use > redirection to set the contents of the file the way you want
```
cat <<EOF > /etc/ssmtp/ssmtp.conf
AuthUser=static1001@googlemail.com
AuthPass=linustorvalds
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
EOF

```

4. i would drop the sleep commands ... why make a script artificially run slower than it needs to

---

### Post by slashwannabe94 on 2010-12-12
Thanks man :) 
I am very new to bash programming. 

I will read and expand what you have told me :) 
thanks dude, :)

---

### Post by slashwannabe94 on 2010-12-12
What do you mean by one step ?

---

### Post by matt_symes on 2010-12-12
Hi

What DaithiF means by test the return value is, after each command that can fail, test its return value.
You can do this by adding...

```
[[ $? -eq 0 ]] || { echo "Failed to do XXX, exiting...; exit 1; }
```..after each command that might fail. $? above contains the return value of the last command executed and || is a logical OR.

This will test the return value and if is not zero (i.e. failure) it will run the second part of the conditional statement. I.E. 

```
echo "Failed to do XXX, exiting...; exit 1;
```It will display 'failed to do XXX' and then exit the script. If the return value is zero then [[ $? -eq 0 ]] will be true and { echo "Failed to do XXX, exiting...; exit 1; } will never be executed.

There was a small typo in there so what you want is... (Notice the extra ").

```
[[ $? -eq 0 ]] || { echo "Failed to do XXX, exiting..."; exit 1; }
```Let me give you an example...

```
#!/bin/bash 

touch /test.sh

[[ $? -eq 0 ]] || { echo "Failed to do XXX, exiting..."; exit 1; }

echo "suceeded"

exit
```As long as this is not run with root permissions it will fail. Running it without root permissions,it will try to create a file (test.sh) on /.

```
touch /test.sh
```This will fail.

```
[[ $? -eq 0 ]] || { echo "Failed to do XXX, exiting..."; exit 1; }
```This checks the return value from touch /test.sh and $? will be non zero so

```
{ echo "Failed to do XXX, exiting..."; exit 1; }
```will be executed, displaying the error message and exiting the script.

```
matthew@matthew-laptop:~/Documents$ ./test_bad_exit.sh
touch: cannot touch `/test.sh': Permission denied
Failed to do XXX, exiting...
```If run as root it will succeed as root can create files in /.

matthew@matthew-laptop:~/Documents$ sudo bash -c ./test_bad_exit.sh 
suceeded
matthew@matthew-laptop:~/Documents$ 

In your situation you would be looking at doing some like...

```

echo "Welcome to sTaTiC's gmail setup..."

echo "Installing SSMTP..."

sudo apt-get install ssmtp

[[ $? -eq 0 ]] || { echo "Failed to install SSMTP, exiting..."; exit 1; }

echo "SSMTP installation complete!"

......


```Hope this helps.

Kind regards

---

### Post by slashwannabe94 on 2010-12-12
[FONT=Arial][SIZE=2]Thank you so much man :D 

Here is the code i have created, edited with the content posted. [/SIZE]

[/FONT]#!/bin/bash


if [ "$(/usr/bin/id -u)" != "0" ]; then
   exec /usr/bin/sudo "$0"
fi

echo "Welcome to sTaTiC's gmail setup..."

echo "Installing SSMTP..."

sudo apt-get install ssmtp

[[ $? -eq 0 ]] || { echo "Failed to install SSMTP, exiting..."; exit 1; }

echo "SSMTP installation complete!"

echo "Installing heirloom-mailx..."

sudo apt-get install heirloom-mailx

[[ $? -eq 0 ]] || { echo "Failed to install heirloom-mailx, exiting..."; exit 1; }

echo "heirloom-mailx installation complete!"

echo "configuring ssmtp.conf..."

[[ -e /etc/ssmtp/ssmtp.conf ]] && cp /etc/ssmtp/ssmtp{.conf,.bak}

[[ $? -eq 0 ]] || { echo "Failed to create backup /etc/ssmtp/ssmtp.conf, exiting..."; exit 1; }

cat <<EOF > /etc/ssmtp/ssmtp.conf
AuthUser=email@gmail.com
AuthPass=password
FromLineOverride=YES
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
EOF

echo "Done!"

exit


Hope its ok dude :P

---

