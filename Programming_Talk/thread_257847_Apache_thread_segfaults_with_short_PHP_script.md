---
title: "Apache thread segfaults with short PHP script"
date: 2006-09-15
forum: Programming Talk
---

### Post by ifokkema on 2006-09-15
Hi Guys && Gals,

I am developing a DNA mutation storage database and under some circumstances the Apache thread(s) crash on me. I've narrowed down the code to a 35 line script with no remaining includes. I've had it crash under Ubuntu Dapper and our Debian Sarge production server.

Here's the script:
[PHP]<?php
function lovd_magicUnquote ($var = '')
{
    // Undoes the magic quoting.
    if (!$var) {
        if (count($_POST)) {
            lovd_magicUnquote(& $_POST);
        }

    } else {
        if (is_array($var)) {
            foreach ($var as $key => $val) {
                if (is_array($val)) {
                    lovd_magicUnquote(& $var[$key]);
                } else {
                    $var[$key] = stripslashes($val);
                }
            }
        } else {
            $var = stripslashes($var);
        }
    }
}

$_POST = array();

// Crashes the Apache thread under GNU/Linux Ubuntu Dapper Apache/1.3.34-2ubuntu0.1 PHP/4.4.2-1build1.
// Also crashes under GNU/Linux Debian Sarge Apache/1.3.33-6sarge1 PHP/4.3.10-16.
$_POST['test'] = array();

// These do not crash.
//$_POST['test'] = array('asdf');
//$_POST['test'] = 'asdf';

lovd_magicUnquote();
?>[/PHP]

When loaded, I get a download dialog, for an empty file (regardless of the actual output the PHP script should send). The Apache error log reads:
```
[Fri Sep 15 09:09:29 2006] [notice] child pid 5015 exit signal Segmentation fault (11)
```
This is GNU/Linux Ubuntu Dapper Apache/1.3.34-2ubuntu0.1 PHP/4.4.2-1build1. On our Sarge production server, it even crashed multiple Apache threads all in once:
```
[Fri Sep 15 10:07:50 2006] [notice] child pid 1195 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:50 2006] [notice] child pid 2925 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:50 2006] [notice] child pid 4263 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:50 2006] [notice] child pid 4264 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:50 2006] [notice] child pid 4378 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:50 2006] [notice] child pid 4379 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:50 2006] [notice] child pid 4538 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:50 2006] [notice] child pid 4885 exit signal Segmentation fault (11)
[Fri Sep 15 10:07:51 2006] [notice] child pid 374 exit signal Segmentation fault (11)
```
That's GNU/Linux Debian Sarge Apache/1.3.33-6sarge1 PHP/4.3.10-16.

- Can anyone tell me if I'm doing something wrong?
- Can anyone tell me if they're having the crash too or not, and either way, on what machine?

Thank you all for your input.

Ivo

---

### Post by ifokkema on 2006-09-15
Tested on another test server... crashes:
```
[Fri Sep 15 15:24:54 2006] [notice] child pid 7936 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:54 2006] [notice] child pid 7939 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:54 2006] [notice] child pid 7940 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:54 2006] [notice] child pid 7943 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:54 2006] [notice] child pid 16728 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:55 2006] [notice] child pid 7941 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:55 2006] [notice] child pid 12825 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:55 2006] [notice] child pid 12826 exit signal Segmentation fault (11)
[Fri Sep 15 15:24:55 2006] [notice] child pid 12827 exit signal Segmentation fault (11)
```

Server specs:
GNU/Linux Debian Unstable Apache/2.0.55-4 PHP/5.1.2-1+b1

The function seems to get into a loop, because if I add a echo statement in the function call, it gets printed lots of times...

---

### Post by nereid on 2006-09-15
Maybe your script has to many recursions. This would be only cause of a segfault that I could find in this script.

---

### Post by ifokkema on 2006-09-15
Hi Nereid,

Thanks for your answer. I agree that this is probably the cause of the crash, since when I add an print() somewhere, it gets printed many times...

The problem is however, it **shouldn't** recurse that much! An array containing an empty array is passed, and a foreach() on an empty array shouldn't do anything...

---

### Post by nereid on 2006-09-16
Why don't you check against

[php]
<?php
$_POST = array();

function test ($a = '') {
	if(!$a) {
		if(count($_POST)) {
			print 'post not empty';
			test(&$_POST);
		} else
			print 'empty';
	} else 
		print 'full';
}

test();
?>
[/php]

This testing code runs fine on my system. Your server should print 'empty' and stop the script. Very confusing.

---

### Post by ifokkema on 2006-09-16
Hi Nereid,

Thank you for the post. Your code is not getting into the loop because it's not recursing the way my script is. I've managed to pinpoint the problem:

[PHP]<?php
function test ($var = '')
{
    if (!$var) {
        print('No argument given : ');
    } else {
        print('Argument given : ');
    }
    var_dump($var);
}

test(array());
?>[/PHP]

This outputs:
```
No argument given : array(0) { }
```
While in my opinion it should've been:
```
Argument given : array(0) { }
```

So an empty array is regarded false. Therefor my function keeps recursing into $_POST and the whole thing comes down. I will need to modify my function to check for ($var === '') or the like.

Thanks for your input!

Ivo

---

### Post by nereid on 2006-09-16
Ok, I tested my version with an empty array

```
test(array());
```

And I get from my function the *empty* code. This was the way I expected the function should work.

So you just should change the if condition. Change the branches and simply ask for

```
if($var) // instead of if(!$var)
```

---

### Post by ifokkema on 2006-09-16
No, well, you see, the function was meant to undo the Magic Quoting setting. When run like lovd_magicUnquote(), without an argument, it will use stripslashes on all $_GET, $_POST and $_COOKIE vars. To make things easier, I only left the operation on $_POST there. Your function does not really recurse into $_POST, it just calls the function with $_POST as an argument and that's it. You can see from my first example code that it needs to recurse into the given variable, if a variable has been given.

That's what went wrong. I checked for if (!$var) but an empty array is regarded false apparently, and if (!$var) returns true. This will cause an infinite recursion into $_POST. To fix this, I must use if ($var === '') in stead of if (!$var). See my previous post.

Ivo

---

### Post by nereid on 2006-09-17
> **ifokkema said:**
> That's what went wrong. I checked for if (!$var) but an empty array is regarded false apparently, and if (!$var) returns true. This will cause an infinite recursion into $_POST. To fix this, I must use if ($var === '') in stead of if (!$var).

This is what I meant, just in a different way ;) But regardless, you've got it working and that's it.

---

### Post by ifokkema on 2006-09-17
> **nereid said:**
> This is what I meant, just in a different way ;) But regardless, you've got it working and that's it.
Ah, OK, great, thanks :)

---

