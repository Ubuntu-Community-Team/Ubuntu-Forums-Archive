---
title: "Help creating script to create php.ini file"
date: 2016-08-17
forum: New to Ubuntu
---

### Post by warren55 on 2016-08-17
I'm trying to write a script to create a php.ini file so I don't have to edit the php.ini each time I do an install.  I'm using Ubuntu 16.04.  I've used filezilla to copy the edited php.ini to my windows 10 computer and I'm using notepad ++ with Edit/EOL set to unix.  I then create the script file with nano in an ssh session and copy the code from the clipboard into the script file in Ubuntu.
```
sudo echo '[PHP]
_;;;;;;;;;;;;;;;;;;;_
; About php.ini   ;
;;;;;;;;;;;;;;;;;;;
; PHPs initialization file, generally called php.ini, is responsible for
; configuring many of the aspects of PHPs behavior.


; PHP attempts to find and load this configuration from a number of locations.
; The following is a summary of its search order:
; 1. SAPI module specific location.
; 2. The PHPRC environment variable. (As of PHP 5.2.0)
; 3. A number of predefined registry keys on Windows (As of PHP 5.2.0)
; 4. Current working directory (except CLI)
; 5. The web servers directory (for SAPI modules), or directory of PHP
; (otherwise in Windows)
; 6. The directory from the --with-config-file-path compile time option, or the
; Windows directory (C:\windows or C:\winnt)
; See the PHP docs for more specific information.
; http://php.net/configuration.file ............

; Local Variables:
; tab-width: 4
; End:' > php.ini
sudo mv php.ini /etc/php/7.0/fpm/

```
This is the error I get
```
sudo echo [PHP]: No such file or directory./c3.sh: line 209: syntax error near unexpected token `;;'
./c3.sh: line 209: `;;;;;;;;;;;;;;;;;;;'

```
The line of code that is underlined is line 209.  I wasn't sure if other ' marks like in php's etc caused a problem so I removed them except from the beginning and end of the code.  Not sure what the issue is.  Thanks in advance.

---

### Post by &amp;KyT$0P# on 2016-08-17
1) [FONT=Courier New]sudo echo '...' > somefile[/FONT] runs the echo command as root but writes to the output file as the normal user.  I usually get around that problem this way:
[FONT=Courier New]rm -fv somefile && echo '...' | sudo tee somefile 1> /dev/null[/FONT]
(leaving out the [FONT=Courier New]1> /dev/null[/FONT] if you actually want it dumped in the terminal screen)

2) Yes other ' marks would be a problem.  When using ' marks then all characters are literal except the ' which is treated as ending the string.
However the error you get indicates that you might have mismatched ' marks in your script right **before** that posted code?

3) What shell are you running it with?  Can you please post the first line of your script (should start with [FONT=Courier New]#![/FONT])?

---

### Post by warren55 on 2016-08-17
1) rm -fv php.ini && echo '......' | sudo tee php.ini 1> /dev/null
is that correct?
3) #!/bin/bash

---

### Post by &amp;KyT$0P# on 2016-08-17
> **warren55 said:**
> 1) rm -fv php.ini && echo '......' | sudo tee php.ini 1> /dev/null
is that correct?
Well, replacing the ...... with your code you have, yes.

> 3) #!/bin/bash
Good. :)

---

### Post by warren55 on 2016-08-17
seems to work thanks.  Any idea by the command 'newgrp www-data' kills the scripts?

---

