---
title: "debugging php from shell"
date: 2006-03-05
forum: Programming Talk
---

### Post by oldmanstan on 2006-03-05
i know you can run php scripts from the command line (i don't know how which is probably my problem) but what i want to do is just debug the script without having to run it on a web server... any simple way of doing this? if it's complicated i'll just do the upload / test thing

thanks!

p.s. also, anybody know what happens when you use the explode function and your separator is repeated twice in a row? does it just skip the blank space or does it return a blank array element?

example
```

$a_string = "hello world";

$new_strings = explode("l", $a_string);

```

since "l" is repeated twice in a row will the array contain ["he", "o wor", "d"] or will it contain ["he", "", "o wor", "d"]? hope i'm explaining myself ok

---

### Post by juvi on 2006-04-23
> **oldmanstan]i know you can run php scripts from the command line (i don't know how which is probably my problem) but what i want to do is just debug the script without having to run it on a web server... any simple way of doing this? if it's complicated i'll just do the upload / test thing
[/QUOTE]

It's actually not that hard.

You just have to get php#-cli.

So if you want to run it in PHP4 (for testing), you'd apt-get install php4-cli

Once you do that, you have to put:
```

#!/path/to/php/

```

at the beginning of your script.

Then just ./blah.php and it will run.

[QUOTE=oldmanstan]
p.s. also, anybody know what happens when you use the explode function and your separator is repeated twice in a row? does it just skip the blank space or does it return a blank array element?

example
```

$a_string = "hello world" said:**
>  or will it contain ["he", "", "o wor", "d"]? hope i'm explaining myself ok

Yes it will return a blank array element.

If you do not wish to have these blank elements, just do a:
```

$new_array = array_diff($array, array(""));

```

hrm, yes that should work, it will only return the array items that are not blank.

Happy coding!

---

### Post by deuce868 on 2006-04-25
I wouldn't suggest debugging via command line though because it uses a different PHP.ini when running via command line so you're debugging might not be valid. For instance running a php file from the command line turns off the timeout limit that you might hit on the actual server.

---

### Post by juvi on 2006-04-26
[QUOTE=deuce868]I wouldn't suggest debugging via command line though because it uses a different PHP.ini when running via command line so you're debugging might not be valid. For instance running a php file from the command line turns off the timeout limit that you might hit on the actual server.[/QUOTE]

I do agree with this.

Perhaps you should be using Eclipse with PHPEclipse installed. It's actually very useful and allows you to debug from inside the IDE. (That's what makes it integrated)

If you need help installing this, google phpeclipse, It's really very easy.

---

