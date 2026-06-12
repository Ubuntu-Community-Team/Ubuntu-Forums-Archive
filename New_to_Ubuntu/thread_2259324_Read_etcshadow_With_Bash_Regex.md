---
title: "Read /etc/shadow With Bash Regex"
date: 2015-01-03
forum: New to Ubuntu
---

### Post by Brian_Strauch on 2015-01-03
I want to extract the username and password fields of the shadow file with a bash script. For example,

**tanderson:$1$AqW8SRi1$Dd0m3hFyOI276/IHinecr0:15652:0:99999:7:::**
Has a username **[COLOR=#000000]tanderson[/COLOR]** and password field [COLOR=#000000]**$1$AqW8SRi1$Dd0m3hFyOI276/IHinecr0**.[/COLOR]

I have figured out how to extract usernames from the file and store them in an array:
**usernames=($(sudo grep -o '^[^:]*' /etc/shadow))**

How do I do the same for the password fields?**&#8203;**

---

### Post by Lars Noodén on 2015-01-03
I would try [awk](http://manpages.ubuntu.com/manpages/trusty/en/man1/awk.1posix.html) to select the lines containing a password and then print out the password.

```

awk 'BEGIN { FS=":" } $2 != "*" & $2 != "!" { print $2 } ' /etc/shadow

```

---

### Post by sisco311 on 2015-01-03
In bash I'd do something like:
```
while IFS=: read -r user pwd _
do
    printf '%s\n%s\n\n' "user: $user" "password: $pwd"
done < /etc/shadow

```
Check out BashFAQ 001 (link in my sig).

But there are many ways and tools to do this. If you tell us what do you want to do with the user names and encrypted passwords, then we can help you with finding the right tool for the job.

---

