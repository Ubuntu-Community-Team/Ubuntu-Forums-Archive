---
title: "bash: check if file size is zero before doing some action"
date: 2019-12-10
forum: Programming Talk
---

### Post by marchello_lippi2 on 2019-12-10
Hi all, 
I'm sending some log to my inbox on regular basis using crontab. Sometimes log is empty and I would like to skip it in this case if possible. 
```
[FONT=monospace][COLOR=#000000]59 0 * * * rm /tmp/rejectlog_filtered.txt; less /var/log/exim4/rejectlog | grep -v "junkemailfilter" > /tmp/rejectlog_filtered.txt; mpack -s "rejectlog_filtered.txt" /tmp/rejectlog_filtered.txt user@example.com[/COLOR]
[/FONT]
```

Another question is, how do I send mentioned log file as message body instead of attachment? (less important for me, but still would like to solve)
Please advise.

---

### Post by sudodus on 2019-12-10
Test with test -s

```

test -s filename

```
If size=0, the test returns 1, otherwise if size>0 test returns 0.

You find more details about test in bash by the command

```

help test

```

---

### Post by marchello_lippi2 on 2019-12-10
Hi sudodus, 
Thanks, I tested it and it should work for me. 
I don't know when it returns 0 and when 1, but below command returns size=0 properly (if file is empty indeed) :
```
$ if test -s /tmp/test.txt; then echo -e "size>0"; else echo -e "size=0"; fi
size=0
```

Upd:
```
$ less /home/user/rejectlog_email.sh
if [ -f "/tmp/rejectlog_filtered.txt" ]; then rm /tmp/rejectlog_filtered.txt; fi

less /var/log/exim4/rejectlog | grep -v "junkemailfilter" > /tmp/rejectlog_filtered.txt

if test -s /tmp/rejectlog_filtered.txt; then mpack -s "some subject" /tmp/rejectlog_filtered.txt [EMAIL="user@example.com"]user@example.com[/EMAIL]; fi
```

---

### Post by sudodus on 2019-12-10
Returning zero means true (or success) while 1 means false (or failure). I think you got it right.

Please notice that [FONT=Courier New][ something ][/FONT] is the same as [FONT=Courier New]test something[/FONT]

---

### Post by marchello_lippi2 on 2019-12-10
Thanks [COLOR=#000000]sudodus.[/COLOR]

---

