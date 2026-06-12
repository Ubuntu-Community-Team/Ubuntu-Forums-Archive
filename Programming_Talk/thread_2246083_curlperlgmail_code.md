---
title: "curl/perl/gmail code"
date: 2014-09-28
forum: Programming Talk
---

### Post by vasa1 on 2014-09-28
Background: I know nothing about curl and very, very little about perl.

If I run```

curl -u username:password --silent "https://mail.google.com/mail/feed/atom" | perl -ne 'print "\t" if /<name>/; print "$2\n" if /<(title|name)>(.*)<\/\1>/;'
``` and I have an unread email with the word **perl** as the subject waiting for me in [email]username@gmail.com[/email], I get```
	Gmail - Inbox for usename@gmail.com</title><tagline>New messages in your Gmail Inbox</tagline><fullcount>1</fullcount><link rel="alternate" href="http://mail.google.com/mail" type="text/html" /><modified>2014-09-28T11:55:52Z</modified><entry><title>perl
```

I'm assuming that curl, when provided with the username and password gets some information from the gmail account and that that information is then piped to perl which in turn prints part of what curl retrieved as output on the screen.

I thought I would try to see all what curl retrieved (before perl did its clean-up) by using ```
curl -u username:password --silent "https://mail.google.com/mail/feed/atom" > curl.txt
```Nothing happened on screen; I had to press Ctrl+C to get back the prompt but a zero byte file called curl.txt was created.

Then I tried```
curl -u username:password --silent "https://mail.google.com/mail/feed/atom" | grep Inbox
```and that gave me```
<?xml version="1.0" encoding="UTF-8"?><feed version="0.3" xmlns="http://purl.org/atom/ns#"><title>Gmail - Inbox for username@gmail.com</title><tagline>New messages in your Gmail Inbox</tagline><fullcount>1</fullcount><link rel="alternate" href="http://mail.google.com/mail" type="text/html" /><modified>2014-09-28T11:55:52Z</modified><entry><title>perl</title><summary>testing curl n perl</summary><link rel="alternate" href="http://mail.google.com/mail?account_id=username@gmail.com&amp;message_id=148bc1d67bf16ad5&amp;view=conv&amp;extsrc=atom" type="text/html" /><modified>2014-09-28T11:55:12Z</modified><issued>2014-09-28T11:55:12Z</issued><id>tag:gmail.google.com,2004:1280480025182953112</id><author><name>My evil twin</name><email>nemo@gmail.com</email></author></entry></feed>
```
My question for now is why does redirecting to curl.txt (as I tried in the third code box from the top) not work?

---

### Post by ian-weisser on 2014-09-28
> **vasa1 said:**
> My question for now is why does redirecting to curl.txt (as I tried in the third code box from the top) not work?

Nothing had downloaded yet.
When the download completes, the script ends and you get a prompt. You hit CTRL+C before that point.

---

### Post by vasa1 on 2014-09-28
> **ian-weisser said:**
> Nothing had downloaded yet.
When the download completes, the script ends and you get a prompt. You hit CTRL+C before that point.Oops! You're right. Thanks!

My next question is this: is it possible to get a prettier output than what curl/perl provides? I suspect not because that would imply doing something akin to parsing xml/html which is frowned upon or which requires special skills/software.

---

### Post by Lars Noodén on 2014-09-28
```

perl -ne 'print "\t" if /<name>/; print "$2\n" if /<(title|name)>(.*)<\/\1>/;'

```

The [-n option](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlrun.1.html) wraps the following code around your short one-liner program:

```

LINE:
                while (<>) {
                    ...             # your program goes here
                }

```

What that does is basically a loop which reads stdin with each iteration line is read and assigned to the pre-defined variable *$_*

And the [-e option](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlrun.1.html) tells perl that the following will be the program.  The */.../* is pattern matching just like in awk.  And the backslashes are there to escape the literal slashes so they don't get interpreted as part of the command.

So this part prints a tab if the line (as represented by [$_ variable](http://manpages.ubuntu.com/manpages/trusty/en/man1/perlvar.1.html)) contains "<name>":

```
print "\t" if /<name>/; 
```

The second part uses parenthesis for grouping the pattern.  The first group looks for "<title>" or "<name>" and the second group finds all characters starting from that first group up to, but not including, a matching "</title>" or "</name>": The \1 represents whatever the first group found.  That's a little complex to follow, but then if it is found, it prints out the second group, that is to say the contents of the tag.

```
print "$2\n" if /<(title|name)>**(.*)**<\/\1>/;'
```

So if it finds "<title>**foo**</title>" or "<name>**foo**</name>" it will print out "foo"

---

### Post by vasa1 on 2014-09-28
@Lars Noodén, thanks for responding. I can't say I understood that with my present level of knowledge but I've come up with something that looks a little more decent than the original curl/perl output which I got from [http://www.commandlinefu.com/commands/view/3386/check-your-unread-gmail-from-the-command-line:](http://www.commandlinefu.com/commands/view/3386/check-your-unread-gmail-from-the-command-line:)```
$ curl -u username:password --silent "https://mail.google.com/mail/feed/atom" | sed 's/></>\n</g' | grep -e fullcount -e title -e summary
<title>Gmail - Inbox for username@gmail.com</title>
<fullcount>2</fullcount>
<title>here's a longer subject line just to see what happens</title>
<summary>And here's some longer text: On 09/27/2014 02:44 AM, Luigi Burdo wrote: &gt; Like the previus on</summary>
<title>perl</title>
<summary>testing curl n perl</summary>
$ 
``` Adding "-e name" and "-e email" at the end will show the poster's name and e-mail address as well.

---

### Post by Lars Noodén on 2014-09-28
The output from Google seems to be an Atom feed, that's just XML.  sed, awk and grep are not so great at parsing XML, but what you are looking for would be the elements between each <entry> and </entry>  Each pair will contain a lot of other elements, the actual elements and number of them will vary depending on what's in your mail box and how many messages are in each thread.   But it will look something like this for each "entry"  

```

<entry>
  <title> ... </title>                                                             
  <summary> ... </summary>                                                         
 <link rel="alternate" href="http://mail.google.com/mail?account_id=..." />
 <modified>... </modified>
 <issued>... </issued>
 <id> ... </id>
 <author>
   <name> ... </name>
   <email> ... </email>
 </author>
 <contributor>
   <name> ... </name>
   <email>... </email>                                                             
 </contributor>
</entry>

```

What did you want extracted and how should it look?

---

### Post by Vaphell on 2014-09-28
just for kicks i whipped up a python3 prog

```
#!/usr/bin/env python3

import sys
import xml.etree.ElementTree as ET

colors = {
             'RED' : '\033[31m',      'LRED' : '\033[91m',
           'GREEN' : '\033[32m',    'LGREEN' : '\033[92m',
          'YELLOW' : '\033[93m',   'LYELLOW' : '\033[93m',
            'BLUE' : '\033[34m',     'LBLUE' : '\033[94m',         
         'MAGENTA' : '\033[35m',  'LMAGENTA' : '\033[95m',
            'CYAN' : '\033[36m',     'LCYAN' : '\033[96m',
            'GREY' : '\033[37m',     'WHITE' : '\033[97m',
            'BOLD' : '\033[1m',
            'ENDC' : '\033[0m'
         }

def print_data( tag, flist, template ):
    values = {}
    for f in flist:
        node = tag.find( '/'.join( xmlns+x for x in f.split('/') ) )
        values[f.replace('/','_')] = node.text
        values.update( colors ) 
    print( template.format( **values ) )

# -----------------

fields = ( 'title', 'tagline', 'fullcount' )
e_fields = ( 'title', 'summary', 'author/name', 'author/email', 'issued' )

template = """{BOLD}{MAGENTA}{title}{ENDC}
{GREEN}{tagline} ({BOLD}{fullcount}{ENDC}{GREEN}){ENDC}"""

e_template = """
{LCYAN}{BOLD}{author_name}{ENDC} <{CYAN}{author_email}{ENDC}>  [{issued}]
{LGREEN}{title}{ENDC}
{summary}"""



data = ''.join( sys.stdin.readlines() )
xroot = ET.fromstring( data )
xmlns = xroot.tag[:xroot.tag.find('}')+1]

print_data( xroot, fields, template )

for e in xroot.findall( xmlns+'entry' ):
    print_data( e, e_fields, e_template )
```

it would be much much shorter if i didn't implement configurable templates with colors.
It works with my gmail account
```
curl -u .... | ./gmail.py
```

---

### Post by vasa1 on 2014-09-28
@Lars Noodén:
> **Lars Noodén said:**
> The output from Google seems to be an Atom feed, that's just XML.  

Yes, I recognized it as xml (I edit ~/.config/openbox/rc.xml by hand) and I recall people saying that parsing xml or html can lead to surprises.

> **Lars Noodén said:**
>  ...What did you want extracted and how should it look?
What got me going was the default output of the curl/perl script. It is just one long line. And not that human-readable.

So what I wanted was 
[LIST]
[*]the number of unread posts (fullcount element)
[*]as much of the subject line that curl grabs (title element)
[*]as much of the body (summary element)
[*]the sender's name
[*]the sender's email address
[/LIST]
on separate lines. The code I have currently does that using curl, sed, and grep.

You have answered my other question [here]("http://ubuntuforums.org/showthread.php?t=2246108&p=13131213#post13131213") and so I'll go back and see if I can use perl instead of sed for the limited purpose of introducing line-breaks (which is all I used sed to do) and decoding whichever entities can be decoded.

---

### Post by vasa1 on 2014-09-28
> **Vaphell said:**
> just for kicks i whipped up a python3 prog
...
.
.
.
It works with my gmail account
```
curl -u .... | ./gmail.py
```
Pretty and awesome! And it seems to take care of at least HTML entities. Of course, there's no chance I'll understand what you've done, so I'm not asking for any explanation!

---

### Post by Vaphell on 2014-09-29
l2python then ;-)
ElementTree module takes care of parsing and unescaping for you.
Once you feed it with data, you get the tidy object tree of xml nodes.
You can look for nodes with find( tag_path )/ findall( tag_path )
If you know a bit of python, look at the module docs and play with some examples it's pretty straightforward.

---

