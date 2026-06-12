---
title: "how would i interface with a webpage in python/perl/ruby"
date: 2009-01-28
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-28
ok so i know the three languages listed above decently to do this, but i need a pointer in the right direction about what libs to use and such

basically i want to interface with a webpage (put text in text box, hit buttons etc)

how would i do that in any of those languages

---

### Post by cardinals_fan on 2009-01-28
[http://www.cs.cf.ac.uk/Dave/PERL/node225.html](http://www.cs.cf.ac.uk/Dave/PERL/node225.html)

---

### Post by WitchCraft on 2009-01-28
> **jimi_hendrix said:**
> ok so i know the three languages listed above decently to do this, but i need a pointer in the right direction about what libs to use and such

basically i want to interface with a webpage (put text in text box, hit buttons etc)

how would i do that in any of those languages

search google for how to write "cgi scripts"

---

### Post by jimi_hendrix on 2009-01-28
ok...(i dont mean on the server side...i mean on my side....like i am typing in this textbox)

---

### Post by myrtle1908 on 2009-01-28
Do you mean you want to simply HTTP POST to a server?  Or do you want to automate/simulate a user using a page?  If the latter, then there are tools for this eg. Selenium, Rational Robot etc.

---

### Post by .Maleficus. on 2009-01-28
You might take a look at a framwork like Rails or Django which handle HTTP requests and the like fairly easily - in Django, you write a model (class) that takes a request "object" and then parses and executes the proper function based on the type of request/model/defined function.  I didn't do a good job explaining but the MVC (Model/View/Controller) pattern it follows is very intuitive and easy to use after a little playing with it.  Rails is the same type of framework (MVC).

---

### Post by jimi_hendrix on 2009-01-29
> **myrtle1908 said:**
> Do you mean you want to simply HTTP POST to a server?  Or do you want to automate/simulate a user using a page?  If the latter, then there are tools for this eg. Selenium, Rational Robot etc.

the latter i believe...basically (this is not what i want to do but its an example) it would be able to make a post here...

---

### Post by ufis on 2009-01-29
So you are looking for the python/perl/ruby alternative to the following javascript? (Rusty javascript so it may not be 100%)
[php]
document.form1.sometextbox.value="This is my text.";
document.form1.submit();
[/php]

---

### Post by jimi_hendrix on 2009-01-29
no...basically im just making a script that will copy the contents of a file to [www.pastebin.com](www.pastebin.com) then hit the send button, and return the url of the paste

---

### Post by ajackson on 2009-01-29
You could try capturing the request that is sent when you click the send button using wireshark and write your app to mimic that send but changing the data sent. The resulting response would, i assume, contain the url that you need.

---

### Post by jimi_hendrix on 2009-01-29
sounds complex (i will try it if there is no other option but...) anyone have any easier means?

---

### Post by imdano on 2009-01-29
You can use curl to easily send the request and get the response, but I think you're still going to have to use a sniffer to figure out what the request should look like.

---

### Post by Reiger on 2009-01-29
If it is 'embedding' a webpage inside your app with rendering & everything; there exist some 3rd party FOSS components for that. KDE is built around that idea of embedding components which provide the functionality in various (GUI) front-ends that provide the 'environment'.

If it is just sending/receiving stuff, wget with a proper user-agent string may do just fine? (Note that it can do HTTP/FTP authentication, POST data etc.)

---

### Post by jimi_hendrix on 2009-01-29
i think imdano's advice was the best...i recored what happened when i sent foo to pastebin.com...but it looks confusing...

---

### Post by sujoy on 2009-01-29
perl and python both have libs for this. mechanize comes to mind.
however i havent been able to get it working in one of my programs.

---

### Post by myrtle1908 on 2009-01-29
This should do it.  Works for me anyways.

[PHP]use strict;
use warnings;
use LWP 5.64;

my $pastebin = 'http://pastebin.com/pastebin.php';
my $browser = LWP::UserAgent->new;
my $response = $browser->post(
   $pastebin,
   [
      code2 => 'public void test() { print "Test\n"; }', # The code
      expiry => 'd', # d=day, m=one month, f=forever
      format => 'java', # Language
      paste => 'Send',
      poster => 'Anon' # Your name
   ]
);

# Prints the pastebin URL for the code you sent
#  eg. http://pastebin.com/d155315d7
print $response->header('Location'); [/PHP]

PS.  All I had to do here was use Firebug to inspect the request to get the POST parameters.  Then I had a look at the response to find the redirect URL in the headers (which is ultimately the new pastebin URL for your code).  After that it was incredibly easy to knock up.

---

### Post by jimi_hendrix on 2009-01-29
thanks...do i need to download something from cpan?

---

### Post by sujoy on 2009-01-29
iirc libwww-perl is required for using LWP.
thats the package name in arch, might be different in ubuntu.

---

### Post by myrtle1908 on 2009-01-29
> **jimi_hendrix said:**
> thanks...do i need to download something from cpan?

Try running the script.  If it whinges about a missing module (namely LWP) then yes, you will need to install it however I have a feeling that you will already have LWP.

---

### Post by NinjaWork on 2009-01-29
just read this:

[http://www.ietf.org/rfc/rfc2616.txt]("http://www.ietf.org/rfc/rfc2616.txt")

and then use your favorite socket lib in your favorite language ;)

wireshare is great, too...if they are using cookies

---

### Post by myrtle1908 on 2009-01-30
> **NinjaWork said:**
> just read this:

[http://www.ietf.org/rfc/rfc2616.txt]("http://www.ietf.org/rfc/rfc2616.txt")

and then use your favorite socket lib in your favorite language ;)

Lol.  Now why would you want to do that?  There is a wealth of HTTP client libraries out there in every language imaginable.  Perl/LWP being one of them.

---

### Post by NinjaWork on 2009-01-30
> **myrtle1908 said:**
> Lol.  Now why would you want to do that?  There is a wealth of HTTP client libraries out there in every language imaginable.  Perl/LWP being one of them.

oh, I know, but it is so much easier just to use IO::Socket and add a few headers :p

---

