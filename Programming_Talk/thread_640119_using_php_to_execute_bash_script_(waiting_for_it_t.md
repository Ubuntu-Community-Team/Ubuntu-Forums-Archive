---
title: "using php to execute bash script (waiting for it to finish)"
date: 2007-12-13
forum: Programming Talk
---

### Post by cszikszoy on 2007-12-13
Hello,

I'm trying to execute a bash script using PHP.

My bash script uses gphoto2 to autodetect the cameras that are connected, then captures an image,

This bash script works fine if I execute it from terminal, or even double clicking from nautilus.

Here's the content of the bash script:
```

#!/bin/bash
args=("$@")
gphoto2 --auto-detect
gphoto2 --capture-image -F 1 -I 1 --filename /home/eckersall/www/temp/camimg/${args[0]}

```

The terminal output is:
```
eckersall@lamp-server:~$ ./www/cam asdf1.jpg
Model                          Port                                            
----------------------------------------------------------
Nikon DSC D40 (PTP mode)       usb:            
Time-lapse mode enabled (interval: 1s).                                        
Capturing frame #1/1...
New file is in location /store_00010001/DCIM/101NCD40/DSC_0125.JPG on the camera
Downloading 'DSC_0125.JPG' from folder '/store_00010001/DCIM/101NCD40'...
Saving file as /home/eckersall/www/temp/camimg/asdf1.jpg                       
Deleting file /store_00010001/DCIM/101NCD40/DSC_0125.JPG on the camera
Deleting 'DSC_0125.JPG' from folder '/store_00010001/DCIM/101NCD40'...

```

and the asdf1.jpg image shows up in the www/temp/camimg/ directory and all is well.

I only run into problems when trying to execute this with php's system() command.  Actually, I get problems executing it with exec(), shell_exec() as well.

When I try to execute this in php, using this code:
```

<?php
echo '<pre>';
$last_line = system('/home/eckersall/www/cam asdf2.jpg', $retval);
echo '
</pre>
<hr />Last line of the output: ' . $last_line . '
<hr />Return value: ' . $retval;

?>

```

PHP seems to start to execute the bash script, but won't wait for it to finish.  The bash script takes a little bit of time, beacuse it has to query the cameras connected, and the capture-image function takes about 3 seconds (to capture, and download the image to the computer).

The PHP page outputs this:
```

Model                          Port            
----------------------------------------------------------
Time-lapse mode enabled (interval: 1s).
Capturing frame #1/1...
For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list , please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --capture-image -F "1" -I "1" --filename "/home/eckersall/www/temp/camimg/asdf2.jpg"

Please make sure there is sufficient quoting around the arguments.

```

Which doesn't make much sense because it executes just fine from the terminal.  The first 2 lines of the php output look correct, but then it should show the camera that's connected.  In bash, this usually takes about .5 seconds to complete, it isn't instantaneous.  Same for the capture-image command.

I'd appreciate it if anyone had any ideas or insight into just what the heck is happening here.  I also appologize for such a long post, but I'm trying to be as thourough as possible.

Also - already checked the php execution time var in php.ini (max_execution_time = 30)

Thanks in advance!

---

### Post by ghostdog74 on 2007-12-13
maybe you can try calling gphoto2 from PHP instead of the bash script?

---

### Post by cszikszoy on 2007-12-14
I've actually tried that, using

```

System(gphoto2 --capture-image -F 1 -I 1)

```

Still, it will execute, but gphoto complains about an error and won't actually take the picture.

However, if I try to execute a command that does not rely on the cameras, or a more instantaneous command, like gphoto2 -v, it'll work just fine.

It seems like php is forcing everything to execute right away, without allowing gphoto to actually finish executing.

still stuck :(

---

### Post by pedro_orange on 2007-12-14
Might be a bit crude but have you tried using a sleep() to ensure that it is infact php not waiting for the shell command to finish?

---

### Post by cszikszoy on 2007-12-14
No such luck.  The sleep function pauses the executiuon of the rest of the php document, but still doesnt change any of the output from gphoto.

---

### Post by geirha on 2007-12-14
Does the php-script have to wait for the commands to finish? you could add an & at the end of the commands. Then system will start the command in the background and return immediately, and the rest of the php-script should be processed.
Example:
[php]system("gphoto2 --capture-image -F 1 -I 1 &");[/php]

---

### Post by sunset_studies on 2007-12-14
which user is the script running as? Could it be as simple as the apache user not having access to your camera?

---

### Post by cszikszoy on 2007-12-14
Thanks for the advice geirha, but no such luck with that.  Still getting the same error output.

sunset_studies: I actually hadn't thought about that.  Can I force apache to run the script or (any other commands) as my user?  Or would there be a better way to just give access to the camera to the apache user?

---

### Post by sunset_studies on 2007-12-14
possibly... just run your php script from the command line instead of via your browser. If it still doesn't work, I don't think there's a permission problem.

---

### Post by geirha on 2007-12-14
sunset_studies's idea sounds plausible. Try ```
sudo -u www-data gphoto2 --capture-image -F 1 -I 1
``` If that doesn't work, it's a permission problem.

---

### Post by cszikszoy on 2007-12-14
:) Looks like we are getting somewhere.  I don't think I've ever been so happy to see something NOT work!  As predicted, when I run the command as the www-data user, it produces the same error output that I can see when running it from the browser.

So now...  How can I fix this?  (Sorry if this is trivial, not quite that well versed in the nix environment yet :confused:)

---

### Post by sunset_studies on 2007-12-14
> **cszikszoy said:**
> :) Looks like we are getting somewhere.  I don't think I've ever been so happy to see something NOT work!  As predicted, when I run the command as the www-data user, it produces the same error output that I can see when running it from the browser.

So now...  How can I fix this?  (Sorry if this is trivial, not quite that well versed in the nix environment yet :confused:)



and when you run it from the command line as your usual user it doesn't work either? Just confirming this.

---

### Post by cszikszoy on 2007-12-14
no, as my user, and as root, it runs fine.

Only wont run as the www-data user.

---

### Post by geirha on 2007-12-15
> **cszikszoy said:**
> :) Looks like we are getting somewhere.  I don't think I've ever been so happy to see something NOT work!  As predicted, when I run the command as the www-data user, it produces the same error output that I can see when running it from the browser.

So now...  How can I fix this?  (Sorry if this is trivial, not quite that well versed in the nix environment yet :confused:)

What exactly does the command(s) do? Is the camera a mass storage device that gets mounted automatically when you plug it in? You either have to make sure www-data has the same access to the camera as your regular user, or allow www-data to run the command as your regular user (or root). The first one would be the best choice in my opinion, but might be the hardest one to figure out.

---

