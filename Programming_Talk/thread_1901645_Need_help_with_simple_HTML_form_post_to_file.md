---
title: "Need help with simple HTML form post to file"
date: 2011-12-29
forum: Programming Talk
---

### Post by ARhere on 2011-12-29
Hello People-who-are-smarter-than-me.  :D

I wanted a way for people visiting my server (*with a simple HTML web page*) to leave me simple one line text messages. I was hoping to use the HTML form command...
```
<p><form name="input" action="***input_action_here***" method="post">
Message: <input type="text" name="user" />
<input type="submit" value="Submit" />
</form>

```
...and have the entered text written to a file called *messages.txt* similar to how the Linux redirect command works
```
echo "hello world" >> messages.txt
```
Sorry but I am an electrical engineer so forgive me if this is HTML 101. :P How can I easily do this?
-AR

---

### Post by nmaster on 2011-12-29
do you have php installed on the web server? this covers a slightly more complicated problem, should definitely help:
[http://www.dreamincode.net/forums/topic/9866-textarea-editor/](http://www.dreamincode.net/forums/topic/9866-textarea-editor/)

PS: im an EE person too :)

---

### Post by HotCupOfJava on 2011-12-29
If you're wanting to write to a file, you're gonna need some sort of server-side language, as nmaster has indicated. Many (but not all) web hosting companies have php running even for their free accounts. Alternatively, you could use Javascript and have the form email you messages from the page.

---

### Post by nmaster on 2011-12-29
if you do something with email (or really in any case) you might want to use reCAPTCHAs to prevent people/bots from screwin' with you:
[http://www.google.com/recaptcha](http://www.google.com/recaptcha)

---

### Post by Lars Noodén on 2011-12-29
Here's a short perl script that reads a single value from HTML form data and then appends that value to a text file.  

```

#!/usr/bin/perl                                                                 

use CGI;        # Common Gateway Interface                                      
use strict;     # restrict sloppy constructs                                    
use warnings;   # enable warnings                                               

my $file = qq(/var/tmp/output.txt);     # text output                  
my $query = CGI->new;                   # new CGI query                         

# HTTP headers and HTML head                                                    

print $query->header( -type=>"text/html", -charset=>"UTF-8" );
print $query->start_html( -title=>"Form output" );

# get values of one single form field (user)                                    

my @values = $query->param('user');

open ( TAB, ">>", $file )
    or die ( "Could not open '$file' for appending: $!\n" );

foreach my $value ( @values ) {
    $value =~ tr/\000-\037/ /s;         # remove control chars if any
    print qq(v=),$value,qq(<br /> \n);
    print TAB $value,"\n";              # output to file
}

close ( TAB );

# Done                                                                       

print qq(</body>\n</html>\n);
exit ( 0 );


```

---

### Post by ARhere on 2011-12-31
Thanks Everyone!

It looks like Perl was the best approach and then Lars Noodén was nice enough to post an example.

-AR

---

### Post by ARhere on 2011-12-31
I jumped the gun on setting this "SOLVED" too soon.

I have the slightly modified Perl code saved as *getmessage.pl* in the same location as the *index.html* that is calling it.  I tried calling the script directly in the **action** HTML field but this does not work.
```

<p><form name="input" action="perl ./getmessage.pl" method="post">
Message: <input type="text" name="usmr" />
<input type="submit" value="Submit" />
</form>

```

---

### Post by Lars Noodén on 2011-12-31
Perl is already called by the line [font=Courier New]#!/usr/bin/perl[/font] so you don't have to call it again.  So if your script is called [font=Courier New]getmessage.pl[/font] and is in the directory [font=Courier New]/usr/lib/cgi-bin[/font] then your form should look like this:

```

<p><form name="input" action="/cgi-bin/getmessage.pl" method="post">

```

That's assuming the defaults for Apache2.

---

### Post by ARhere on 2011-12-31
> **Lars Noodén said:**
> Perl is already called by the line [font=Courier New]#!/usr/bin/perl[/font] so you don't have to call it again.  So if your script is called [font=Courier New]getmessage.pl[/font] and is in the directory [font=Courier New]/usr/lib/cgi-bin[/font] then your form should look like this:

```

<p><form name="input" action="/cgi-bin/getmessage.pl" method="post">

```

That's assuming the defaults for Apache2.

Location issue, I had the getmessage.pl script in my /var/www/ location.  Moving to /usr/lib/cgi-bin/ fixed it, thank you.

One last thing please.  I would like to have the Perl script enter a line break, then current date+time, then the message. Just in case I forget to check the file for a while.  When I get home I will open a Perl book to learn more.  :D

Thanks again Lars,
-AR

---

### Post by Lars Noodén on 2011-12-31
Then I would add a little to the script:

```

#!/usr/bin/perl                                                                 

use CGI;        # Common Gateway Interface                                      
use strict;     # restrict sloppy constructs                                    
use warnings;   # enable warnings                                               

my $file = qq(/var/tmp/output.txt);     # tab-delimited output                  
my $query = CGI->new;                   # new CGI query                         

# HTTP headers and HTML head                                                    

print $query->header( -type=>"text/html", -charset=>"UTF-8" );
print qq(<!DOCTYPE html                                                         
    PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"                             
     "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">                 
<html xmlns="http://www.w3.org/1999/xhtml" lang="en-US" xml:lang="en-US">       
 <head>                                                                         
  <title>Form output</title>                                                    
 </head>                                                                        
);

my ($s,$m,$h,$day,$mon,$year) = localtime();
$year += 1900; 
$mon++;

# get values of one single form field (user)                                    
my @values = $query->param('user');

open ( TAB, ">>", $file )
    or die ( "Could not open '$file' for appending: $!\n" );

foreach my $value ( @values ) {
    print qq(v=),$value,qq(<br /> \n);
    print TAB qq($year-$mon-$day $h:$m:$s\t),$value,"\n";
}

close ( TAB );

# Done                                                                          

print qq(</body>\n</html>\n);
exit ( 0 );

```

The "Camel Book" is essential and the Cookbook is useful.  If you want to change the location of your scripts look at the part of your Apache configuration around "ScriptAlias"

---

### Post by ARhere on 2011-12-31
Perfect.  Need to modify to make the date more human readable but a little Google has me working on that already.

Thank you again!
-AR

---

