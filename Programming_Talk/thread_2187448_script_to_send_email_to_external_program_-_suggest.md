---
title: "script to send email to external program - suggestions"
date: 2013-11-12
forum: Programming Talk
---

### Post by steve.potts on 2013-11-12
Hi all,

I want to pass an email to external program, my current script is basic, as you can see, and for some reason it fails on certain emails (the texts come through blank :( )
but for some emails its okay.

Id be interested to hear any other ways you think i could do this? 

Thanks in advance.

#!/usr/bin/perl
$num='07777123456';
use Mail::Internet;
$msg=Mail::Internet->new(\*STDIN);
$head=$msg->head;
$subject=$head->get('Subject');
$body=$msg->body;
chomp($subject);
$txt=substr(join("\n",($subject,@$body)),0,640);
$txt=~s/\s*$//;
system("/bin/echo \"$txt\"\ | /usr/bin/gammu-smsd-inject TEXT \"$num\" -len 640 > /dev/null 2>&1");

---

### Post by TheFu on 2013-11-12
Is this for SMS?  Isn't the character limit 140 characters, not 640?  If you send too much ... empty?

---

### Post by steve.potts on 2013-11-12
nah it should send a multipart once it goes over the limit.

---

