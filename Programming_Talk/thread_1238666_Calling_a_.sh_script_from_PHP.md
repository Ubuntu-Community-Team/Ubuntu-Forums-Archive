---
title: "Calling a .sh script from PHP"
date: 2009-08-12
forum: Programming Talk
---

### Post by jtrulen on 2009-08-12
I have a script that I am trying to run via PHP after the user uploads a file.

I have tried using system(), exec(), as well as shell_exec() without success.

I have sudoers modified to allow my script ( transfer.sh ) to run as root without a password already as well as changed the permissions on transfer.sh to 777.

I am running out of ideas. Anyone else got any ideas for me to try?

Thanks in advance,

JTrulen

---

### Post by CyberJack on 2009-08-12
Do you get any error's? 
Did you try to add a return/output variable to exec and system to check for errors?

---

### Post by jtrulen on 2009-08-12
No errors and I tried adding an output variable to it and print it to the screen. Nothing showed up.

---

### Post by CyberJack on 2009-08-12
Can you run the file as web user from a terminal? (www-data if you used the default installation)

---

### Post by jtrulen on 2009-08-12
Anyone can run the file via web, at least once it is working.

I just tried to run the script via a terminal window and it worked flawlessly.

---

### Post by jtrulen on 2009-08-12
I don't know if it helps at all, but the file is located in: /opt/lampp/htdocs/Uploads/transfer.sh

The site uploads a file, creates the script transfer.sh based on the file, then runs the file, in which moves the file over to a different directory.

---

### Post by CyberJack on 2009-08-12
Does this help: [http://nl3.php.net/manual/en/function.exec.php#85930](http://nl3.php.net/manual/en/function.exec.php#85930)
He needed to pass the full path to the exec file before getting any output.

---

### Post by jtrulen on 2009-08-12
I am passing the full path to exec().

Below is my call:

exec( "/opt/lampp/htdocs/Uploads/transfer.sh" );

---

### Post by CyberJack on 2009-08-12
hmm, oke... I just ran out of ideas (it's late already).

You talked about running the script as root (sudoers file), but your call runs the script as web user (www-data).

Can you try something like:
exec("/usr/bin/sudo /opt/lampp/htdocs/Uploads/transfer.sh");

---

### Post by jtrulen on 2009-08-12
Just tried that, but it still refuses to function.

---

### Post by CyberJack on 2009-08-12
After a bit of googling it turns out that you don't get an output when there is an error. Can you try the following:

$command = '/usr/bin/sudo /opt/lampp/htdocs/Uploads/transfer.sh';
$output = exec($command . ' 2>&1', $output, $return);

and see whats in $output and $return?

---

### Post by jtrulen on 2009-08-12
$output = [sudo] password for nobody:
$return = 1

And I have no idea what that means. I'm fairly new to Linux.

---

### Post by jtrulen on 2009-08-12
Ok, so I've narrowed it down to an error in creating a symbolic link in the destination folder as my script tries to do. And I know how to fix that.

Thank you so much for your help CyberJack.

---

### Post by jtrulen on 2009-08-12
Problem is now fully solved. I just had to change the permissions for the destination folder to allow for writing from non-root users.

Probably not the most secure way, but since this will only be used within the companies intranet, I'm not too worried about it.

---

### Post by CyberJack on 2009-08-12
Nice :)

---

### Post by jtrulen on 2009-08-13
I have included the code if anyone else later wishes to do the same thing that I have done. Enjoy!

[PHP]<?php
    
    $target_path = "files/"; // Where the file is going to be placed 
    
    $basename = basename( $_FILES['uploadedfile']['name'] ); // Simplifies calling the basename;

    $target_path = $target_path . $basename; // Add the original filename to our target path.
    
    $success = move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path); // Acually moves file to desired location
    
    $myFile = "yourscript.sh"; // What you want to call your script
    $fh = fopen($myFile, 'w') or die("can't open file"); /* Opens the file ( Overwrites previous, helpful 
                                                         to already have a file created even if it is blank */
    
    $stringData = "..."; // Your Script goes here

    fwrite($fh, $stringData); // Writes to the desired file

    fclose($fh); // Closes and saves the file
    
    $command = '/Full/Path/To/Script/yourscript/sh'; // Your full path to the shell script
    $output = exec($command); // Executes the script

?>[/PHP]

~JTrulen

---

