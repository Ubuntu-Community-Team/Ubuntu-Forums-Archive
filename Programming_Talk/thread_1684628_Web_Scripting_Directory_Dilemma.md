---
title: "Web Scripting Directory Dilemma"
date: 2011-02-09
forum: Programming Talk
---

### Post by skytreader on 2011-02-09
I'm sorry if I'm missing something dead basic but my problem is as follows:

So, in web scripting (I'm using PHP as a vehicle for exposition), I often specify relative URLs in my includes like

```

include("scripts/php/phpfile.php");

```

All is well until I create subdirectories to keep my pages organized. Say, from my root folder, I create a folder "accounts", the pages in the folder "accounts" will have includes of the form

```

include("../scripts/php/phpfile.php");

```

Here on, if I create more subdirectories (say, "admins" in "accounts") I would have to add more of the .. operator. I only have one template file, at the root, containing an include of the form like the first one above. Manually adding the .. operator to all my includes will be tedious and will probably result to errors.


So, I created a simple script that will determine how far in am I in my subdirectory nesting, and will generate the ..'s needed automatically. All I have to do is concatenate. Pretty fine, however (this might sound like a joke but please try not to laugh) ...

... that script will also have to depend on an include. including it into the pages in my subdirectories leads to the problem I just "solved".


So, am I just being over OC with my code? I know that managing a single include (the one for my solution script) is lots better than managing *all* includes but a little more abstraction won't hurt right? How do I work around this?

Thanks!

---

### Post by skytreader on 2011-05-15
Answered my own question (got it months ago actually, so just to do kindness on anyone who might stumble here).

Set the include_path of your php.ini . Or, better yet, if you don't want to deal with system settings, call the function [set_include_path]("http://php.net/manual/en/function.set-include-path.php").

(I don't know if there are any trade-offs between the two in terms of performance. I edited my php.ini, by the way, and must still experience using set_include_path.)

Case closed.

---

