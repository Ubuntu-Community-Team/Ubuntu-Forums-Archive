---
title: "Troouble shooting my script problems"
date: 2015-07-24
forum: Programming Talk
---

### Post by Janet_Cavendish on 2015-07-24
Hi, I’m trying to write a script that creates a user account in Linux and adds it to an appropriate group (either staff or students). However, when it is run, it keeps coming up with the message “unexpected token error ‘done’” . Below, you will find the pseudocode and my actual script, so that you have a rough idea about what I think the script should be doing. Please could you read through and give me a vague idea (so I can sort it out myself) about where I went wrong? Any help will be appreciated.  Also, a final note to say that I’m relatively new to Linux and this is my first script, hence if my script make absolutely no sense whatever, try not to be surprised! (although, I have tried to include as much information as possible to explain my aim)
```
 
**Pseudocode**
START
echo "Enter desired username and press ENTER"
read and store input as $username
If username already exists…
echo "User already exists" and ask for username again
If username is asked for more than 3 times, then exit script
 
echo "Enter desired password and press ENTER"
Read and store variable $password
If password exists…
  echo "Password already exists" and ask for password again
If password is asked for more than 3 times, then exit script
If user is not root, then
echo “Only root can add user" and exit
else encrypt password
add user and Save the user’s details in the /etc/passwd directory
if details found in /etc/passwd directory, then 
echo “User has been added”
else echo “Error: User not added” and try to add user
If an error has occured while trying to add the user more than 3 times, then start script from the beginning again
else (continue)
echo “Is $username a student? (ENTER yes/no)”
Read, create and store variable $confirm
if $confirm = yes; then
groupadd students
else
groupadd staff
END

```
                                                           
```
 
**ACTUAL CODE**
#!/bin/bash
repeat=0
#setting variable for repeat
while test "$repeat" -le "3”
#Repeat the whole script while $repeat is less than or equal to 3
do
#start of main script loop
count = 3
#setting variable for count which is used to repeat username input if the username exists
while test "$count" -le "3"
# Repeat the whole username process while $count is less than or equal to 3
do
#Start of username loop
echo "Enter desired username and press ENTER"
#asking to input username
read $username
#read and store input as $username
                                    if id -u $username >/dev/null 2>&1; then
                                    #If username already exists…
                                    echo "User already exists"
                                    #Output “User already exists"
                                    count=$[count-1]
                                    #Take one away from $count, so that the loop can only happen 3 times
                        done 
#End of count loop
                        exit 0
                        #exit only if username is set and doesn’t exist
else
#Continuation of if then else loop, only continues if username doesn’t exist already 
#Going on to setting the password loop as username variable is set already
passcount=0
#setting variable for passcount which is used to repeat password input if the password exists
while test "$passcount" -le "3"
# Repeat the whole password process while $passcount is less than or equal to 3
do
#Start of password loop
echo "Enter desired password and press ENTER"
#Asking user to input password
read $password
#Read and store variable $password
if id -u $password >/dev/null 2>&1; then
#If password exists…
                                                            echo "Password already exists"
                                                            #Output "Password already exists"
                                                            passcount=$[passcount+1]
#Take one away from $passcount, so that the loop can only happen 3 times
done
#Exit when $password is set and doesn’t already exist
else
#Continuation of the if then else loop
if [ "$(id -u)" != "0" ]; then
#If user is not root, then 
                                                                        echo "Only root can add user" 1>&2
                                                                        #Echo only root can add user
                                                            exit 0
                                                                        #Exit immediately as they are not root
else
#Continuation of the if then else loop
#Only goes on if they are root
pass=$(perl -e 'print crypt($ARGV[0], "password")' $password)
#Encrypt password
useradd -m -p $pass $username
#Add user 
egrep "^$username" /etc/passwd >/dev/null
#Save the user’s details in the /etc/passwd directory
if id -u $username >/dev/null 2>&1; then
            #If user is added
                                                                                    echo "$username has been added!"
                                                                                    #Output that information to user
                                                                                    else
echo ”Failed to add $username!"
#Continuation of the if then else loop if user is not added
added=0
#Set and store variable $added
while test "$added" -le "3"
#Starting loop so that user can be added again
do
useradd -m -p $pass $username
#Adding user
                                                                                                added=$[added+1]
                                                                                                #Adding 1 to added so that the loop repeat only 3 times
done
#Ending the while loop after adding user has been repeated 3 times
                                                                                                            if $added = 3; then
                                                                                                            #If the added loop has repeated 3 times 
repeat=$[repeat+1]
#Then start it from the beginning again
           #Adding 1 to $repeat loop
done
#End of repeat loop. If user not created starts again
 
else
#Continuation of if then else loop
#Only goes on if user created
echo “Is $username a student? (ENTER yes/no)”
#Output option for group
read $confirm
#Read, create and store variable $confirm
if $confirm = yes; then
#If user is a student, then
groupadd student
#Add to the student group
else
#If user is not a student…
groupadd staff
#Add to staff group
fi
#End of loop
                                                                                                            fi
                                                                                                            #End of loop
                                                                                    fi
                                                                                    #End of loop           
                                                                        fi
                                                                        #End of loop
                                                           
fi
#End of loop
                                    fi
                                    #End of loop
Exit 0
#End of shell script

```

---

### Post by SeijiSensei on 2015-07-24
I think you have an extra unmatched "done" in one of the while loops.

Also, I suggest you use indentation so you can clearly see the beginning and end of structures like "do/done" or "if/then/fi".  Perhaps you have them in the original, but the only way to preserve spacing here is to put your code inside [noparse]```

```[/noparse] tags.  It would make it much easier for us to read and comment.

---

### Post by steeldriver on 2015-07-24
Some more general advice: ***start small, and test as you go***

In this case, you have a ~100 line script, yet I can spot at least two errors just in the first 10 lines

```

#!/bin/bash
repeat=0
#setting variable for repeat
while test "$repeat" -le "3[COLOR=#ff0000]**”**[/COLOR]      <-- non-ascii double-quotes **”** (possibly copy-pasted from somewhere)
#Repeat the whole script while $repeat is less than or equal to 3
do
#start of main script loop
count[COLOR=#ff0000]** = **[/COLOR]3                         <-- space around the assignment operator, will be interpreted as a *command *called count with arguments = and 3
#setting variable for count which is used to repeat username input if the username exists

```

---

### Post by PaulW2U on 2015-07-24
Hi Janet_Cavendish

Please use code tags for terminal output - if you are using New Reply button - highlight text and use the # button in the text box header.

If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by Janet_Cavendish on 2015-07-28
Thanks for correcting me, I'll do that next time :)

---

### Post by Janet_Cavendish on 2015-07-28
Thanks for the advice...I've realised maybe this is all a case of trying to go too big without being completely solid on my basics (like checking through for simple errors etc)
Will also start testing small in the future!!

---

### Post by Janet_Cavendish on 2015-07-28
> **SeijiSensei said:**
> I think you have an extra unmatched "done" in one of the while loops.

Also, I suggest you use indentation so you can clearly see the beginning and end of structures like "do/done" or "if/then/fi".  Perhaps you have them in the original, but the only way to preserve spacing here is to put your code inside [noparse]```

```[/noparse] tags.  It would make it much easier for us to read and comment.

Will do that next time, thanks for the advice. I'm sorry I didn't reply earlier but I had already used up my limited data, and hence couldn't post. I highlight that ALL your advice is deeply appreciated, and hopefully my script (once edited) will run as intended.

---

### Post by Vaphell on 2015-07-28
```
Exit 0
```

shells are case sensitive, it's *exit.*

```
if $confirm = yes;
```

not going to work, use if [[ $confirm = yes ]]

even though this *$[] *math is recognized, it's considered obsolete and non-kosher. Use (()) / $(()) intended for integer math instead

valid, tidy alternatives to * count=$[count-1]*:

```
(( count-- ))
(( count -= 1 ))
(( count=count-1 ))
count=$((count-1))
```


also conditions doing integer comparisons can be done in a much more readable way

```
while (( repeat < 3 ))
```


also why prompt user for the details and then disqualify for non-root privileges? Test for root first, print 'this script requires sudo, kthxbye', exit 1 if failed, ask user for details if not. Wasting user's time is unergonomic.

---

