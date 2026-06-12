---
title: "Perl all command-line args (argv)"
date: 2008-10-30
forum: Programming Talk
---

### Post by Felson on 2008-10-30
I am trying to find a way to get "all" the arguments that were typed on the command-line when my script was executed, and I need them to be "exactly" as they were typed. That is, I want the single and double quotes, and the escaping exactly as it was. Anyone know of a way to get this?

---

### Post by snova on 2008-10-30
It can't be done in any language. The shell performs the escaping, not the program. By the time it reaches Perl it's too late.

By the time it reaches exec() it's too late...

---

### Post by Felson on 2008-10-30
Damn. I was afraid that was the answer... That makes writing a warper program a bit harder... :)

---

### Post by snova on 2008-10-30
What's that?

---

### Post by Felson on 2008-10-30
Needed to write a program to wrap tar. It's being executed on a webserver where I have no ssh/telnet access (GoDaddy). Couldn't use tar directly because it timesout to fast. Here is what I ended up doing instead.
```

#!/usr/bin/perl

$Test = 0;
$pid = fork();

if ($pid == 0)
{
 if(!$Test)
 {
   open STDIN, ">>", "/dev/null";
   open STDOUT, ">>", "/dev/null";
   open STDERR, ">>", "/dev/null";
 }

 $args = "";
 for($c = 0; $c < @ARGV; $c++)
 {
   $tmpStr = $ARGV[$c];
   $tmpStr =~ s/"/\\"/g;
   $args .= qq| "$tmpStr"|;
 }

 $command = qq~tar $args > /dev/null 2> /dev/null~; if($Test) {print "$command<br>\n";} else {`$command`;}
 if(!$Test) {exit(0);}
}

```

Kinda simplistic, but it "should" work for anything I will though at it.

---

