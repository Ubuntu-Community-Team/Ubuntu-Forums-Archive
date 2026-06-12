---
title: "Perl and wget"
date: 2010-01-26
forum: Programming Talk
---

### Post by PurposeOfReason on 2010-01-26
I really don't know what's wrong here. I would just use LWP::Simple but the server we have to use at school doesn't have that. If I replace the scaler $URL in the wget with an actual URL it works just fine.

```

#!/usr/bin/perl
use CGI ':standard';
print header;
print start_html;
$count = 1;
$URL = param('URL');
system("wget -O url.txt $URL");
open(INFILE, "url.txt") || die "Cannot open $URL";
while (<INFILE>) {
    if ($_ =~ m/\"(http:\/\/.*?.)"/) {
        print br, "[URL# $count:] <a href=\"$1\">$1</a>";
        $count = $count + 1;
    }
}
close(INFILE);
end_html;

```

---

### Post by Trumpen on 2010-01-26
if $URL contains metacharacters (i.e. &), then you have to protect it during system() call:

[php]system("wget -q -O url.txt \"$URL\"");[/php]

---

### Post by PurposeOfReason on 2010-01-26
I did forget about that but it still doesn't run. I get a 

[http://:](http://:) Invalid host name.

Which is what I had before so I'm sure the syntax is all good, just something funny with wget is going on. Just a slight update to consistency. It could be that since it is run through cgi that the end user doesn't have permissions to create url.txt?

```

#!/usr/bin/perl
use CGI ':standard';
print header;
print start_html;
$count = 1;
$URL = param('URL');
system("wget -O url.txt \"$URL\"");
open(INFILE, "url.txt") || die "Cannot open $URL";
while (<INFILE>) {
    if ($_ =~ m/\"(http:\/\/.*?.)"/) {
        print br, "[URL# $count:] <a href=\"$1\">$1</a>";
        $count = $count + 1;
    }
}
close(INFILE);
system("rm url.txt");
end_html;

```

---

### Post by Some Penguin on 2010-01-26
Your regular expression looks odd to me.  One thing that you might not have considered:  the period is a special character, and * does not mean 'any character'; it's the Kleene star.

You might have more luck with something like


/"(http:\/\/(?:[^\."]+)\.(?:[^\."])(?:[^"]*))"/

(hand-rolled, untested)

which would look for "http://", followed by at least one character which must not be a period or quote, followed by one period, followed by at least one character which must not be a period or quote, then followed by zero or more characters which are not quotes, then bounded by quote.   The quoted stuff ends up in $1.  It will accept some things that are not actually legal URLs (e.g. http://$4.99, if bounded by quotes), but you can modify the character ranges if you like (replacing the 'excludes' groups with groups of characters that are actually allowed, for instance).

---

### Post by PurposeOfReason on 2010-01-26
I tested the regex on an index.html I downloaded and it grabs what it needs to. Tried yours, still got the same problem.

---

### Post by PurposeOfReason on 2010-01-27
Bit of progress, tried running it from the script that calls it and get this:

**Software error:**

 Cannot open [http://www.google.com](http://www.google.com) at /home/****/public_html/cgi_bin/proj2/perl2_1_rec.cgi line 12.  For help, please send mail to the webmaster ([EMAIL="cs.support@wwu.edu"]cs.support@wwu.edu[/EMAIL]), giving this  error message  and the time and date of the error. 



I also threw in a ls -l in there to see if it even wgets the file which it doesn't.

---

### Post by PurposeOfReason on 2010-01-27
The school server had a few issues that are now fixed.

---

