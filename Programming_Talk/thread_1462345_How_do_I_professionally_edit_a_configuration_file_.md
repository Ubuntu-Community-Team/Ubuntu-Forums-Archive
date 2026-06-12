---
title: "How do I professionally edit a configuration file from a script?"
date: 2010-04-25
forum: Programming Talk
---

### Post by shaggy999 on 2010-04-25
I am trying to figure out how to edit some configuration files from a script. As an example I'll use the /etc/ssh/sshd_config file. It has the following lines I would like to change:

Port 22
PermitRootLogin yes
#PasswordAuthentication yes

My current method looks like this:

```

sed -i 's/Port 22/Port 2222/g' /etc/ssh/sshd_config
sed -i 's/PermitRootLogin yes/PermitRootLogin no/g' /etc/ssh/sshd_config
sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config

```

The thing I don't like about this method is that I have to search for the entire line followed by replacing the entire line and it has to match perfectly. For example, what if the Port value was set to 23 or I forgot there was a # sign on the PasswordAuthentication line? That value would then not be changed. I would like to be able to say something like "find the line that starts with 'Port', then change the entire line to 'Port 2222'" -- that seems more flexible to me.

What say you?

---

### Post by Reiger on 2010-04-25
If you simply want to spit out configuration files by far the easiest way would be:

```

template() {
  echo "template file here";
}

template($args) > $file;

```

---

### Post by diesch on 2010-04-25
As *sed* uses regular expressions you can do thinks like[FONT=monospace]

[/FONT]```
[FONT=monospace]sed -i 's/^Port .*/Port 2222/g' /etc/ssh/sshd_config[/FONT]
```

---

### Post by shaggy999 on 2010-04-25
> **diesch said:**
> As *sed* uses regular expressions you can do thinks like[FONT=monospace]

[/FONT]```
[FONT=monospace]sed -i 's/^Port .*/Port 2222/g' /etc/ssh/sshd_config[/FONT]
```

This is better, although I still have to remember that there's a # at the beginning of a line, but that may be my only option as the example file has the text "PasswordAuthentication" written in it multiple times and only in one instance do I want it changed. Thanks.

---

### Post by soltanis on 2010-04-25
That sed code will ignore lines that have a # sign in front. Only if the line starts with "Port " followed by some characters will the script change it.

Since there should only be one Port line in the file, it the script will only change those instances where the line is present and active in the configuration.

---

### Post by shaggy999 on 2010-04-25
Yes, that's what I was saying that I have to remember if there's a # at the beginning of the line when I execute my sed statement. The carat symbol anchors the regex to the beginning of a line. I'll just have to put in a way to test for the # at the beginning of the line and then an if-else clause around the sed execution.

---

### Post by diesch on 2010-04-26
Use[FONT=monospace]
[/FONT]```
[FONT=monospace]sed -i 's/^#?Port .*/Port 2222/' /etc/ssh/sshd_config
```

Regular expressions are quite powerful.
[/FONT]

---

### Post by shaggy999 on 2010-04-26
*face slap*

Oh man, I feel dense. I used to write regular expressions all the time when I wrote perl code. But that was like 2 semesters in college 6 years ago. Damn, I need to study up on this stuff. Thanks.

---

