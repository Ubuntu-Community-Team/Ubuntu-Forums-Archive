---
title: "Shell script help - need help with variables"
date: 2012-12-22
forum: Programming Talk
---

### Post by josiahrulez on 2012-12-22
So, if i input a command into terminal and it gives back some information how can i use that information in the script?

i made an example in pseudocode.
```

ubuntu ()
{
echo You are running Ubuntu
}

linuxmint ()
{
echo You are running Linux Mint
}

suse ()
{
echo You are running OpenSUSE
}



lsb_rlease -a
if "Distributor ID" is equal to ubuntu
	or xubuntu
		or edubuntu
			or lubuntu
				then run ubuntu function
	or if "Distributor ID" is equal to "linux mint"
		then run linuxmint function
	or if "Distributor ID" is equal to suse
		then run suse function
	else 
		print "what version of linux are you running?"
			$userinput=
				print you are running $userinput linux 



```

i want to do something similar to that in my script, but i dont know how. Can someone help me or point me to a wiki page that will?

---

### Post by Vaphell on 2012-12-22
to capture the output of command you need to use $(), eg

```
distro=$( lsb_release -a )
if [ "$distro" = "Suse" ]; then ...
```

---

### Post by josiahrulez on 2012-12-22
> **Vaphell said:**
> to capture the output of command you need to use $(), eg

```
distro=$( lsb_release -a )
if [ "$distro" = "Suse" ]; then ...
```

how would it work with the or command where it can match up to any one of 4 items, also the variable has a space in it, will it work the way i did it "$Distributor ID"?

```

lsb_rlease -a
if "Distributor ID" is equal to ubuntu
	or xubuntu
		or edubuntu
			or lubuntu
				then run ubuntu function

```

```

"Distributor ID"=$ ( lsb_release -a )
if "$Distributor ID" = "ubuntu"; or "xubuntu"; or "edubuntu"; or "lubuntu"; then ubuntu
	if "$Distributor ID" = "linux mint"; then linuxmint 

```
or would it be more like this?
```

"Distributor ID"=$ ( lsb_release -a )
if "$Distributor ID" = "ubuntu"; then ubuntu
	if "$Distributor ID" = "xubuntu"; then ubuntu
		if "$Distributor ID" = "edubuntu"; then ubuntu
			if "$Distributor ID" = "lubuntu"; then ubuntu 
				if "$Distributor ID" = "linux mint"; then linuxmint 

```

---

### Post by ofnuts on 2012-12-22
> **josiahrulez said:**
> So, if i input a command into terminal and it gives back some information how can i use that information in the script?

i made an example in pseudocode.
```

ubuntu ()
{
echo You are running Ubuntu
}

linuxmint ()
{
echo You are running Linux Mint
}

suse ()
{
echo You are running OpenSUSE
}



lsb_rlease -a
if "Distributor ID" is equal to ubuntu
    or xubuntu
        or edubuntu
            or lubuntu
                then run ubuntu function
    or if "Distributor ID" is equal to "linux mint"
        then run linuxmint function
    or if "Distributor ID" is equal to suse
        then run suse function
    else 
        print "what version of linux are you running?"
            $userinput=
                print you are running $userinput linux 



```i want to do something similar to that in my script, but i dont know how. Can someone help me or point me to a wiki page that will?
```

distributorID=$(lsb_release -is)
case distributorId  in
    Ubuntu)
         ubuntu();;
    OpenSuse)
         openSuse();;
     *)
         echo "Unrecognized distribution";;
esac

```

---

### Post by josiahrulez on 2012-12-22
so you both gave me two different ways of doing this, is there a wiki page on this topic? So i can understand what i'm doing instead of copying you.

---

### Post by sisco311 on 2012-12-22
Check out the Bash Guide from my signature. ;)

[http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29)

and BashFAQ 066 (link in my signature).

---

### Post by josiahrulez on 2012-12-22
> **sisco311 said:**
> Check out the Bash Guide from my signature. ;)

[http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29)

and BashFAQ 066 (link in my signature).

Thanks for the links

---

