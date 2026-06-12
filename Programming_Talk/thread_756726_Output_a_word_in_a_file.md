---
title: "Output a word in a file"
date: 2008-04-16
forum: Programming Talk
---

### Post by lexarrow on 2008-04-16
Hi all,

Here's my problem:

I made a script that downloads, installs and configures LDAP from source
I created a user input variable with the base dn ( eg. dc=example,dc=com) . Now I want to automatically create and add an init.ldif file and I need to output `example` from `dc=example,dc=com` to a file

I looked at cat and grep help but I couldn't find the answer.

Any suggestions?

THX!

---

### Post by ghostdog74 on 2008-04-16
to output something to a file from a script, use the ">" or ">>" (append) operator. Otherwise, describe your problem more clearly, providing example inputs and output.

---

### Post by sisco311 on 2008-04-16
```
sed -i 's/^dc=example*/&,dc=com/' filename
```this command will append the lines, in the file *filename*, starting with *dc=example *with *,dc=com* 

dc=example -> dc=example,dc=com

---

### Post by lexarrow on 2008-04-16
I rephrase a little. I have set a variable like this:

```
dialog --title "LDAP Server Configuration" --backtitle "Server Install" --inputbox "Enter the desired BASE of the LDAP server" 8 60 2>/tmp/basedn
basedn=`cat /tmp/basedn`
```

I need a way to output the first word after `dc=` in /tmp/basedn

---

### Post by risby on 2008-04-16
There are many many ways to do this. The most obvious use cut or awk or perl.

To extract the first occurrance of "example" from the string "dc=example -> dc=example,dc=com" held in file /tmp/basedn and store it in variable basedn use any of:
```

basedn=$( cut -d'=' -f2 /tmp/basedn | cut -d' ' -f1 )

basedn=$( awk -F'=' {'print $2'} /tmp/basedn | awk -F' ' '{print $1}' )

basedn=$( perl -ple 's/dc=(.*?) .*/$1/' /tmp/basedn )

```

---

### Post by ghostdog74 on 2008-04-16
no need to call awk that many times. 
```

# more tmp
dc=example,dc=com
# awk -F"[,=]" '{print $2}' tmp
example

```

---

### Post by WW on 2008-04-16
Or sed...
```

basedn=$( sed 's/^dc=\(.*\),.*/\1/' /tmp/basedn )

```
This assumes that /tmp/basedn has just one line of text.

---

### Post by risby on 2008-04-17
> **ghostdog74 said:**
> no need to call awk that many times. 
```

# more tmp
dc=example,dc=com
# awk -F"[,=]" '{print $2}' tmp
example

```

Interesting but that doesn't work in the same way on either my HP-UX or Linux systems:
```

$ cat /tmp/basedn                      
dc=example -> dc=example,dc=com
$ awk -F"[,=]" '{print $2}' /tmp/basedn
example -> dc
$ 

```and that is what I would expect. It uses the first two field separators it finds, i.e. in this case both '=' symbols and returns all the text between them.

Your awk appears to be broken ! EDIT: Ah I see you are using a different input example from the OP.

So
```

awk -F"[ =]" '{print $2}' /tmp/basedn

```would work nicely.

RE-EDIT: Oh dammit, I've re-read the spec, it was my input example that was wrong.

---

