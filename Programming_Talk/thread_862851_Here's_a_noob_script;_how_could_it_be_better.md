---
title: "Here's a noob script; how could it be better?"
date: 2008-07-17
forum: Programming Talk
---

### Post by ConMan318 on 2008-07-17
Alright, since I had never written anything in a language besides Bash that interacted with my OS (besides file I/O and piping and whatnot, you know what I mean) and have been trying to think of fun coding stuff to do, I decided to code an alarm program in Perl.  Keep in mind I don't know that much Perl but I just read a chapter on regex (I'm on chapter 9 of "Learning Perl" :p), so I wanted to put it to use.  The first thing that popped into my head was an alarm program.  It checks every second whether the alarm time set by the user equals the system clock time (most likely not ideal).  If so, it turns up the volume and plays a song.

```

$alarm = "21:35:20";
$done = 0;
while(!($done)){
    if(`date` =~ m/(\d{2}:\d{2}:\d{2})/){
        if($1 eq $alarm){
            $done = 1;
        }
    }
    `sleep 1`;
}
`aumix -v100`;
`gnome-open ~/path/to/song.ext`;

```

Keeping in mind I want to use Bash commands minimally and do not want to use 'cron' for the timing, how could this be improved upon?

I'm not married to the regex idea either, it was just the inspiration for the code.  I would like to keep it in Perl, though.

Any comments/input welcome, thanks!

---

### Post by King_Killa on 2008-07-17
Why not do sleep 60, or even sleep 300.. just make the alarm only work right on the minute, or on 5 minute intervals? It would save a lot on processing. I'd probably ditch the regex completely and just stick with timestamps.. but that's probably just because I've always hated working with regex.

---

### Post by unutbu on 2008-07-17
This removes the need to call `date` and `sleep`:

```
#!/usr/bin/perl
use strict;
use warnings;

my $alarm = "23:09:00";
my $done = 0;
while (!$done) {
    my ($sec,$min,$hour,$mday,$mon,$year,$wday,$yday,$isdst) = localtime;
    my $date=sprintf "%02d:%02d:%02d", $hour,$min,$sec;
    if ($date eq $alarm) {
	$done = 1;
    }
    sleep(1);
}

```

Edit: I agree with King_Killa, there is no real need for a loop -- once you know the localtime you can compute how many seconds you need to sleep...

---

### Post by |{urse on 2008-07-17
very nice! you should include an xmessage popup with a "Good Morning _________ !" and a button that turns it off

---

### Post by ConMan318 on 2008-07-17
Thanks for posting the 'localtime' command; I didn't know of that and it's very helpful.  The reason I didn't calculate the time to sleep (besides that I would have had to parse the regexed time string for hrs/mins/sec since I didn't know the localtime command) is because I didn't know how accurate it was over longer time periods.  Does it use the system clock to keep track of sleep time or is it doing it of its own accord?

I suppose I can test it tonight.  If anyone has any ideas for simple little projects like this that I could try to code, please post those here, too.

---

### Post by rikxik on 2008-07-18
When using perl, lets use its idioms:

```

$alarm = "07:59:02";
sleep(1) until($alarm eq (sprintf "%02d:%02d:%02d", reverse((localtime)[0..2])));

```

HTH

---

