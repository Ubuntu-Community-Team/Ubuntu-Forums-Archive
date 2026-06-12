---
title: "Is my Perl broken, or am I missing something here?"
date: 2011-03-07
forum: Programming Talk
---

### Post by spillin_dylan on 2011-03-07
I am writing a Perl script to try and find my external IP address.  I have parsed a HTML page down to one line containing the IP address, along with some text.  This line of text is saved within a variable.  I am having problems getting the numbers out of this variable using regex.  Here is what I have:

```
      $ipaddr = `wget --quiet --tries=3 -O - http://checkmyip.com/ | grep id=\"ip\"` ;  # Get the IP address, and put it in a variable.
      $_ = $ipaddr;
      /.*(\d.*\d).*$/;
      print $1 . "\n";
      exit 0;
```

I think that the \d should match the first and last digits in the variable (greedy matching) and the brackets should put it into variable $1.  But when I try this out I get:
```
Use of uninitialized value $1 in string at /home/spillin/bin/newipnotify.pl line 95.

```

Sorry if I'm missing something obvious here, but I'm still learning....

Thanks!  
-spillin

---

### Post by Some Penguin on 2011-03-07
I wouldn't write the expression that way; if greediness is done left-to-right, you'll get the last two digits in the string.  In addition, since you're not using ^, the leading .* is only likely to be harmful.

Given the syntax of the response

```

/>(\d+\.\d+\.\d+\.\d)</

```

seems more promising.

---

### Post by spillin_dylan on 2011-03-07
Thank you very much!  I think that was my problem, or close to it anyhow.  I fiddled with your code, and was still not getting results until I realized that there should be one extra plus sign near the end, as it was looking for a pattern with only one digit at the end.  

```

/>(\d+\.\d+\.\d+\.\d[COLOR="Red"]+[/COLOR])</

```

Anyhow, I finally got it working.  It might not be the prettiest Perl script ever, but I bet it's not the ugliest, either!  Thanks Some_Penguin for the help!!!

---

