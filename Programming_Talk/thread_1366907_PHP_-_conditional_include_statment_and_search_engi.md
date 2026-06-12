---
title: "PHP - conditional include statment and search engine referencing"
date: 2009-12-28
forum: Programming Talk
---

### Post by Biochem on 2009-12-28
Hi,
I'm trying to build a small website that will support multiple languages. The idea is to have visitors welcome page that will ask which language they want and set a session variable and a cookie with the information and then display  the page acordingly.

Therefore the actual pages contents is always:

```
<?php
if($_SESSION["lang"]=="en") include(substr($_SERVER["DOCUMENT_ROOT"].$_SERVER['PHP_SELF'],0,-4).".en.php");
if($_SESSION["lang"]=="fr") include(substr($_SERVER["DOCUMENT_ROOT"].$_SERVER['PHP_SELF'],0,-4).".fr.php");
?>
```
So my question is:
Will the actual contents of the pages be referenced in google and other search engins?
If not is there a workaround? I like the idea of having a single URL for the same contents in all languages.

---

### Post by The Secret on 2009-12-28
[robots.txt]("http://www.robotstxt.org/orig.html#examples") ?

---

### Post by Biochem on 2009-12-29
I though robots.txt was to restrict crawlers from visiting parts of a websites. I want the opposite.

Rereading my first post it might lack some important details.

The way I'm designing my site is if the session variable is not set and the cookie doesn't exist the visitor is redirected to the welcome.php page where he is ask if he prefers french or english in a form. when he clicks on the submit button, he is automatically redirected to the page he asked in the first place, which is now displayed in the requested language. 

Since google crawlers will never have the session variable set nor the cookie I fear they will only see the welcome.php page :( .

---

### Post by iMisspell on 2009-12-29
This will not help with your question, but just an opinion about your code...

your substr() does not make sence to me (subtracting 4 but the file you are calling is 6 long), but using switch() might be a better choice. 
Not knowing excatly what your doing, this might also help you with your crawler "welcome.php" problem/thought.

If no session is set, you can set a default file to load (there are other ways to do this also, one switch is less confusing and more readable *to me* for something like this, you could use a bunch of if conditions like you have started).

Instead of redirecting people, you could have a "header link", a link on all pages which will let the user change langs as they please.


[PHP]

    switch( $_SESSION["lang"] ) {
            
            case 'en':
				$file='en.php';
                break;
                
            case 'fr':
				$file='fr.php';
                break;
                
            default:
                $file='en.php';
                break;
    }
    
    include(substr($_SERVER["DOCUMENT_ROOT"].$_SERVER['PHP_SELF'],0,-4) . $file);

[/PHP]


[edit]
If you post exactly what you are doing, using a database or not, willing to use a data-base if not, dynamic or static pages, how many pages, type of site, any and everything ;) maybe people will be able to give you more ideas and suggestions.

What you are doing is fairly common, so im sure you will get feed back.

_

---

### Post by Hellkeepa on 2009-12-29
HELLo!

First a couple of comments, on both the design of the system and the code posted in this thread. I'll take the design first.

What I would have done if I were you, **Biochem**, is to move all of the language into its own file. Let the HTML-files be language-agnostic, and use a template engine to put in the correct language content where it's meant to go. Also, I'd make the language-detection general and dynamic, instead of one line per language as you got now. Will make it much easier to maintain, and lessen the possibilities of bugs in that particular part of the code.
Noted, there are some times where you got so much content that you want to make the whole page language-specific, but this can be solved in a better way. Use the same detection methods when including the template-files, and see if there is any language-specific version before trying to include the general one. No more editing the main code just to add a simple page. ;-)

As for the code that's been posted above, I wouldn't recommend using either of them. Not only is there a complete lack of security, but it also fails on the flexibility test as described above. I've taken the liberty of throwing together some code showing the general basis of how I've done it: [http://pastebin.com/fb681900](http://pastebin.com/fb681900)
Mind you, this code is taken from my own framework, so there's a lot of functionality not shown in this example.

**iMisspell**: "substr ($String, 0, -4)" does not limit the string to 4 chars in length, it drops off the 4 last characters off the end of the string. In this case, the ".php" extension, so that he can add his own language-specific extension.

Happy codin'!

---

