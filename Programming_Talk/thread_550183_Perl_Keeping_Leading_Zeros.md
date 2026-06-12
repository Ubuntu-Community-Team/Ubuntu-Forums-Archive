---
title: "Perl: Keeping Leading Zeros"
date: 2007-09-13
forum: Programming Talk
---

### Post by Hase on 2007-09-13
There might be better places to ask but I already have an account here and like this ravenous crowd.

So, I have a script that uses an incrementing variable within a filename.  That filename is generated using a leading zero for the digits "01" through "09."  When I increment in the script, it drops the leading zero off rendering the script unable to locate the file.

```
for ($day = 01; $day < 31; $day++) {
        system ("ssh remote_machine \"cat /log/reports/$year/$month/$day/summary_$year-$month-$day.txt | grep -v 'whatever'\" >> $temp_file 2>/dev/null");

```

Thanks!?

---

### Post by pmasiar on 2007-09-13
[http://perldoc.perl.org/functions/sprintf.html](http://perldoc.perl.org/functions/sprintf.html) - on first page when you [http://www.google.com/search?q=perl+number+formatting](http://www.google.com/search?q=perl+number+formatting)

---

### Post by Hase on 2007-09-13
```
for ($day = [COLOR="Red"]"[/COLOR]01[COLOR="Red"]"[/COLOR]; [COLOR="Red"]"[/COLOR]$day[COLOR="Red"]"[/COLOR] < 31; $day++) {
        system ("ssh remote_machine \"cat /log/reports/$year/$month/$day/summary_$year-$month-$day.txt | grep -v 'whatever'\" >> $temp_file 2>/dev/null");
```

---

### Post by Hase on 2007-09-13
> **pmasiar said:**
> [http://perldoc.perl.org/functions/sprintf.html](http://perldoc.perl.org/functions/sprintf.html) - on first page when you [http://www.google.com/search?q=perl+number+formatting](http://www.google.com/search?q=perl+number+formatting)

Thanks, I was googling the wrong thing for two hours.

I think that the solution I stumbled across is much more straight forward though, since I'm not trying to "re"-format, just keep formatting.

---

### Post by pmasiar on 2007-09-13
I know how it hurts: You know **exactly** that answer is trivial, but for hour cannot whip up decent keywords for Google... :-( Doing it all the time, always learn something new unexpectedly... :-)

---

### Post by bashologist on 2007-09-14
Those lines are very long, you could maybe split them up a bit like this.
```
for ($day = 1; $day < 31; $day++)
{
	$file = sprintf "/log/reports/$year/$month/%02d/summary_$year-$month-$day.txt", $day;
	system ("ssh remote_machine \"cat '$file' | grep -v 'whatever'\" >> $temp_file 2>/dev/null");
}

```

---

### Post by Hase on 2007-09-14
I'll play around with that on Monday.  Thanks all!

---

