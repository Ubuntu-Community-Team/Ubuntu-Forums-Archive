---
title: "escape commands in bash script parameter"
date: 2007-12-28
forum: Programming Talk
---

### Post by thor918 on 2007-12-28
Hi there!
is it possible to remove all sort of code injection in a parameter?

I have this ultra simple code, that uses the bash parameter in another command.
I don't want that the user has the possibility to write for example
./mybashscript '-al;rm -r /dir/;'
```

#
#!/bin/bash
#
if [ -z "$1" ]; then
echo 'ERROR'
exit 1
else

/bin/ls $1 #do command
error=$? # Preserve the exit code

if [ $error != 0 ]; then
echo 'ERROR'
else
echo 'OK'
fi
fi

```

---

### Post by ghostdog74 on 2007-12-28
> **thor918 said:**
> Hi there!
is it possible to remove all sort of code injection in a parameter?

I have this ultra simple code, that uses the bash parameter in another command.
I don't want that the user has the possibility to write for example
./mybashscript '-al;rm -r /dir/;'
```

#
#!/bin/bash
#
if [ -z "$1" ]; then
echo 'ERROR'
exit 1
else

/bin/ls $1 #do command
error=$? # Preserve the exit code

if [ $error != 0 ]; then
echo 'ERROR'
else
echo 'OK'
fi
fi

```

That's bad design. What do you actually want to do? where did '-al;rm -r /dir/;' come from?

---

### Post by thor918 on 2007-12-28
>That's bad design. What do you actually want to do? where did '-al;rm -r /dir/;' come from?
the code you see there, is just an example. so it's all test data. you see?

the thing is being used in a php-webpage, and I have to use it to get the exit code of the program I'm executing. It sound strange perhaps. but php looses the exitcode of a process when I use a crucial phpcode. so this is my workaround. I agree it's not a perfect way to do it. the PHP page has offcource  escaped possible injections, but I want also to limit what the bash script can take as an argument.
I should be possible to limit what a bash script accepts as an argument?

and if the bashscript is bad designed, how would you construct the bash script to take arguments that is foolproof to not take injected code?

edit:
hmm. it seems the code isn't running the injected code.
I did probably test it wrong.

the bash would infact execute it as
/bin/ls '-al;rm -r /dir/;'
and ls would just report bad command.

:p sorry about that. I'm not that steady on bash scripting

---

### Post by ghostdog74 on 2007-12-28
> **thor918 said:**
> >That's bad design. What do you actually want to do? where did '-al;rm -r /dir/;' come from?
the code you see there, is just an example. so it's all test data. you see?

the thing is being used in a php-webpage, and I have to use it to get the exit code of the program I'm executing. It sound strange perhaps. but php looses the exitcode of a process when I use a crucial phpcode. so this is my workaround. I agree it's not a perfect way to do it. the PHP page has offcource  escaped possible injections, but I want also to limit what the bash script can take as an argument.
I should be possible to limit what a bash script accepts as an argument?

and if the bashscript is bad designed, how would you construct the bash script to take arguments that is foolproof to not take injected code?

technically, yes, you are able to, using a combination of string manipulation/regular expressions. If you really need to execute external shell program because PHP can't do it ( which i doubt) , a better and more secure approach would be to give your users no chance to key in something. all they can do is only tick what you give them. Just like an ATM. you get my point?

---

### Post by thor918 on 2007-12-28
it's not that php can't do it, it's just how it works that won't cut it for me.
the command "proc_get_status" will just clear any exitcode that exists for the process, when I close it:
$return_value = proc_close($process);... from what I read, this is by design. if I execute the command trough the bash script the exit code is preserved, and I'm happy. that's the short story.

any way it seems like I was mistaken that it was possible to inject code in my bash script like it is now.
an expert pointed that out for me just a minute ago.
the whole parameter is executed as a whole quoted parameter for the ls command.
witch will make ls command just report wrong arguments. so it seems I'm safe on injections on that script, from what I see. 


thanks for the input ;)

---

