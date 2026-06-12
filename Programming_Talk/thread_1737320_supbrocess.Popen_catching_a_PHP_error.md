---
title: "supbrocess.Popen: catching a PHP error"
date: 2011-04-23
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-04-23
Hi there,

I'm running a PHP command from a Python script and I want to catch the error when the computer is not connected to internet. In practice however, the script returns the result when it works but it doesn't return the error.

The script has this format:

```
result = subprocess.Popen(['my', 'php', 'command', 'line'], stdout=PIPE).stdout
display = result.read()
print display
```

In case of an error it returns: ''

Alternatively i tried:

```
result = os.popen('my php command line').readlines()
print result
```

which, in case of error, returns []

Interestingly:

```
test = suprocess.call('my php command line', shell=True)
print test
```

returns 0, which means subprocess thinks the command succeeded.

If i run my PHP command line (it's fbcmd by the way) while offline, i get the error message: 

[FONT="Courier New"]PHP Warning:  fopen(): php_network_getaddresses: getaddrinfo failed: Name or service not known in /usr/local/lib/fbcmd/facebook/facebookapi_php5_restlib.php on line 3272[/FONT]

etc... (it's a long one)

Is there anyone who knows how i can catch that error? It would be nice :)
(I could indeed use the empty string as an error signal, but that wouldn't be good for my learning process :) )

Thanks!
Benjamin

---

### Post by Zugzwang on 2011-04-23
Two things:

First of all try if the PHP interpreter sets an error code. For checking this, execute your PHP script from the command line and then hit "echo $?" in the shell. Does it show 0? Then, the PHP interpreter indeed doesn't set an errorlevel.

Second, programs typically write error output to stderr and not stdout. Thus, if you want to read the errors, you should pipe that stream (and read from the pipe) as well.

---

### Post by jesuisbenjamin on 2011-04-23
Thanks Zugzwang, i'm new to this :)

So [FONT="Courier New"]echo$?[/FONT] returns [FONT="Courier New"]255[/FONT].

And indeed if i replace stdout by stderr, i can read the message error.

Now there's one thing i don't understand: before i execute the command i am not supposed to know what will be the result (either success or failure) so why should there be a different channels for each and how can i collect either result?

Thanks.
Benjamin

---

### Post by MadCow108 on 2011-04-23
> **jesuisbenjamin said:**
> Thanks Zugzwang, i'm new to this :)

So [FONT="Courier New"]echo$?[/FONT] returns [FONT="Courier New"]255[/FONT].

And indeed if i replace stdout by stderr, i can read the message error.

Now there's one thing i don't understand: before i execute the command i am not supposed to know what will be the result (either success or failure) so why should there be a different channels for each and how can i collect either result?

Thanks.
Benjamin

printout to stdout does not always indicate success nor does stderr always indicate failure.
The exit code is used for that in well behaved applications.

to get all:
```
p = subprocess.Popen(..., stdout=subprocess.PIPE, stderr=subprocess.PIPE)
stdout, stderr = p.communicate()
error_code = p.returncode

```

---

### Post by jesuisbenjamin on 2011-04-23
Thanks MadCow108 :)

---

