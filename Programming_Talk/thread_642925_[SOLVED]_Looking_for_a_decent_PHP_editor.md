---
title: "[SOLVED] Looking for a decent PHP editor ?"
date: 2007-12-17
forum: Programming Talk
---

### Post by jbt on 2007-12-17
Hi,

I'm trying to find something similar to Dreamweaver. but for linux.
I only have a simple list of requirements:
1) I want to be able to have several windows open and see them all.
   e.g. tile them.
2) Syntax highlighting
3) Help on functions/parameters as I type would be nice
4) WYSIWYG Preview would be nice/

I've tried:
Quanta Plus
Kompozer
Bluefish
emacs

Emacs comes closest, but it doesn't do the function hints, and I was hoping for something a little more modern. I was using emacs when I first started to program 25 years ago!

Quanta comes next, but I can find a way to tile the edit windows, or get rid of many parts of the screen bloat.

Blufish reminds me of Paint on windows, very clunky and also no multiple windows.

Kompozer wont even edit php files, it just opens the file in Bluefish.

I find it hard to believe that the best Linux has to offer is a 25 year old text editor :-(

Anything else I should try before I resort to running Dreamweaver in a virtual machine ?

Thanks
JohnT

---

### Post by LaRoza on 2007-12-17
> **jbt said:**
> 
I find it hard to believe that the best Linux has to offer is a 25 year old text editor :-(

Anything else I should try before I resort to running Dreamweaver in a virtual machine ?
T

The best is a text editor. The stability and development of Emacs makes it very good, although I am a Vim user, which is even older.

I don't understand what a WYSIWYG editor for PHP is supposed to do, are you mixing code with markup?

You can review the links in the stickies, just in case something was mentioned before.

---

### Post by emilioastarita on 2007-12-17
Eclipse?

And you can try the another php-mode for emacs:
[http://code.google.com/p/mewde/](http://code.google.com/p/mewde/)

---

### Post by jbt on 2007-12-17
> **LaRoza said:**
> The best is a text editor. The stability and development of Emacs makes it very good, although I am a Vim user, which is even older.


Emacs was VERY good in its time, and still is for a lot of jobs, but it was designed for machines that were about 100 times slower that modern machines. I was hoping that all those extra megahertz  might be able to provide something more than some pretty menus.

> **LaRoza said:**
> 

I don't understand what a WYSIWYG editor for PHP is supposed to do, are you mixing code with markup?


Of course !
That is what PHP is for.

If I wanted to keep the code and markup seperate I would use something better suited, like Perl.

> **LaRoza said:**
> 
You can review the links in the stickies, just in case something was mentioned before.

Yes, I already did a search and found the editors I've already tried.

Regards
JohnT

---

### Post by LaRoza on 2007-12-17
> **jbt said:**
> 
Of course !
That is what PHP is for.

If I wanted to keep the code and markup seperate I would use something better suited, like Perl.
T

I don't use it that way....

Just because PHP allows you to make such code, that doesn't mean you should.

It has nothing to do with the language, just how it is used.

---

### Post by jbt on 2007-12-17
> **LaRoza said:**
> I don't use it that way....

Just because PHP allows you to make such code, that doesn't mean you should.

It has nothing to do with the language, just how it is used.


From [www.php.net:](www.php.net:)
[INDENT]
**What is PHP?**

PHP is a widely-used general-purpose scripting language that is especially suited for Web development and can be embedded into HTML[/INDENT]. 

PHP was developed specifically to allow code to be embedded with the markup. Thats what its good at. You CAN use it for other stuff, but most people use it for what it was intended.

---

### Post by jbt on 2007-12-17
> **emilioastarita said:**
> Eclipse?

That looks like it could be good - if I was developing Java.
Seems to be very much oriented to Java development.

> **emilioastarita said:**
> 
And you can try the another php-mode for emacs:
[http://code.google.com/p/mewde/](http://code.google.com/p/mewde/)


Sounds good, but I couldn't finda way to extract the .7z files :-(

---

### Post by bvanaerde on 2007-12-17
about your reply on Eclipse
> **jbt said:**
> That looks like it could be good - if I was developing Java.
Seems to be very much oriented to Java development.
That's not quite true... Eclipse can be used for PHP also.

Some links that might interest you:
[LIST]
[*]PHPEclipse: [http://www.phpeclipse.net](http://www.phpeclipse.net)
[*]Aptana: [http://www.aptana.com/](http://www.aptana.com/) (Eclipse based)
[/LIST]

---

### Post by Samjiman on 2007-12-17
> **LaRoza said:**
> I don't use it that way....

Just because PHP allows you to make such code, that doesn't mean you should.

It has nothing to do with the language, just how it is used.

PHP can indeed be used for projects not involving a grain of HTML or in fact anything to with the web. It's just its most commonly used for server side scripting on the web.

PHP if I remember what I've read correctly, was originally designed to be a set of tools, to replace his original Perl scriptsl, for the original developer's  home page. In fact I think PHP, originally stood for Personal Home Page and that the current name P HyperText Processor is what it is called due to its evolution into a proper language.

---

### Post by LaRoza on 2007-12-17
I use PHP for the web, also ECMAScript, CSS and XHTML. See [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

That site doesn't mix any of the above, on the client or the server. It is very, very easy to maintain (yes, it is small). 

The PHP templates I have make it easy for me to make a new site in seconds, and I don't have to pick through code.

(The site is actually one page, index.php)

Python and Perl can be used like PHP is commonly used with a little work, but that is a bad practice.

---

### Post by scruff on 2007-12-17
I use Komodo for all my Perl and Python development. It does PHP and a number of other things as well. It's about as close to say Visual Studio that I have found. For Perl and Python it integrates a GUI debugger, has version control built in, and a bunch of other cool stuff. I have the full version, but I think there is a new free version as well.

---

### Post by lessthanphil on 2007-12-17
Have you had a look at "Kate". I know it is part of KDE (KDE Advanced Text Editor) but it runs under Gnome fine, it's absolutely brilliant for PHP in my opinion and I've been using it commercially and personally for a few years.

---

### Post by Natr0n on 2007-12-17
There's [Nvu]("http://nvudev.com/index.php") as well.

---

### Post by Majorix on 2007-12-18
I will just go ahead and say that PHP is actually really slow in interpreting the code. I had a link that compared the speed and ram issues in many different languages and their compilers/interpreters, and PHP was way behind some other scripting languages like Perl and Python. Considering how these both languages I mentioned also be compiled to max the speed up, you can see what I mean (hopefully). Why do you have to write the markup language and the coding language in the same file?

---

### Post by jbt on 2007-12-18
> **bvanaerde said:**
> about your reply on Eclipse

That's not quite true... Eclipse can be used for PHP also.

Some links that might interest you:
[LIST]
[*]PHPEclipse: [http://www.phpeclipse.net](http://www.phpeclipse.net)
[*]Aptana: [http://www.aptana.com/](http://www.aptana.com/) (Eclipse based)
[/LIST]

Apparently, but it didn;t seem that easy to make it happen, and I don't think it would do anything that Quanta+ can't do.

---

### Post by jbt on 2007-12-18
> **lessthanphil said:**
> Have you had a look at "Kate". I know it is part of KDE (KDE Advanced Text Editor) but it runs under Gnome fine, it's absolutely brilliant for PHP in my opinion and I've been using it commercially and personally for a few years.

That just seems to be a text editor.
I can do better than that with emacs.

---

### Post by lamalex on 2007-12-18
GEANY!!!
How the hell has no one suggested this yet? It's what you've been looking for in an IDE for uh.. any language. I use it mainly for PHP and Python. Seriously try it, it's in the repos, you'll **** yourself.

---

### Post by jbt on 2007-12-18
> **Majorix said:**
> I will just go ahead and say that PHP is actually really slow in interpreting the code. I had a link that compared the speed and ram issues in many different languages and their compilers/interpreters, and PHP was way behind some other scripting languages like Perl and Python. Considering how these both languages I mentioned also be compiled to max the speed up, you can see what I mean (hopefully). Why do you have to write the markup language and the coding language in the same file?

It maybe not the most efficient language, but I've never had problems with PHP performance on any of the projects I have used. Network bandwidth is normally the limiting factor.

I started off writing C CGI scripts and I know from experience that using PHP is much quicker to develop.

Putting the code in with the markup makes things MUCH easier to maintain.
You don't have to change things in multiple places, and it is much easier to generate dynamic websites. You end up generating html and javascript with the code, so it is much nicer to have it in there with the rest of it.

---

### Post by LaRoza on 2007-12-18
> **jbt said:**
> Putting the code in with the markup makes things MUCH easier to maintain.
You don't have to change things in multiple places, and it is much easier to generate dynamic websites. You end up generating html and javascript with the code, so it is much nicer to have it in there with the rest of it.

You mix JavaScript with markup too?

I separate the content of the site from the code that makes it work. To change the content, it is very easy, you don't have to sift through code (except XHTML), and to change or add features, you don't have to sift through content.

---

### Post by ThinkBuntu on 2007-12-18
> **Majorix said:**
> I will just go ahead and say that PHP is actually really slow in interpreting the code. I had a link that compared the speed and ram issues in many different languages and their compilers/interpreters, and PHP was way behind some other scripting languages like Perl and Python. Considering how these both languages I mentioned also be compiled to max the speed up, you can see what I mean (hopefully). Why do you have to write the markup language and the coding language in the same file?
PHP is widely recognized as one of the fastest options when it comes to server-side processing. It's without a doubt faster than Python and Ruby, and probably slower than Java and ASP.NET (compiled). That being said, any language can be made very fast or very slow depending on the programmer.

---

### Post by LaRoza on 2007-12-18
> **ThinkBuntu said:**
> PHP is widely recognized as one of the fastest options when it comes to server-side processing. It's without a doubt faster than Python and Ruby, and probably slower than Java and ASP.NET (compiled). That being said, any language can be made very fast or very slow depending on the programmer.

PHP is much faster than CGI, and Perl and Python can be used for CGI, however, they can also be used in the same manner as PHP, so I doubt there is a speed difference. I don't know about Ruby.

---

### Post by jbt on 2007-12-20
> **jbt said:**
> Hi,

I'm trying to find something similar to Dreamweaver. but for linux.
I only have a simple list of requirements:
1) I want to be able to have several windows open and see them all.
   e.g. tile them.
2) Syntax highlighting
3) Help on functions/parameters as I type would be nice
4) WYSIWYG Preview would be nice/

I've tried:
Quanta Plus
Kompozer
Bluefish
emacs




Quick Status report - 

After trying out most of suggestions by the various posters, I have decided on Quanta Plus, and have been using it  for a couple of days.

Although it does have some drawbacks - such as not being able to view multiple source windows, it does have many benefits and nice features too.

I would advise people coming from using Dreamweaver to give it a serious look. It does take a while to get used to it, but I think a few days of patience does pay off in the end.

Thanks for everyone advice and comments.

Regards
JohnT

---

