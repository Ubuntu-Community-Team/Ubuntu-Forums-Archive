---
title: "PHP:  Email File Attachments"
date: 2008-10-30
forum: Programming Talk
---

### Post by s.fox on 2008-10-30
Hi.

I have been going insane for the last few hours trying to figure out why the PHP code below dosen't work.  Its supposed to take an array of files and send them in an email attachment.  The email is sent but doesn't contain any attachments.

```
      <?php

      // array with filenames to be sent as attachment

      $files = array("output.pdf","Plan.pdf");

      // email fields: to, from, subject, and so on

      $to = "a@a.com";

      $from = "b@b.com";

      $subject ="Multiple Attachments";

      $message = "This email has several attachments!";

      $headers = "From: $from";

      // boundary

      $semi_rand = md5(time());

      $mime_boundary = "==Multipart_Boundary_x{$semi_rand}x";

      // headers for attachment

      $headers .= "\nMIME-Version: 1.0\n" . "Content-Type: multipart/mixed;\n" . " boundary=\"{$mime_boundary}\"";

      // multipart boundary

      $message = "This is a multi-part message in MIME format.\n\n" . "--{$mime_boundary}\n" . "Content-Type: text/plain; charset=\"iso-8859-1\"\n" . "Content-Transfer-Encoding: 7bit\n\n" . $message . "\n\n";

      $message .= "--{$mime_boundary}\n";

      // preparing attachments

      for($x=0;$x<count($files);$x++){
 
          $file = fopen($files[$x],"rb");

          $data = fread($file,filesize($files[$x]));

          fclose($file);

          $data = chunk_split(base64_encode($data));

          $message .= "Content-Type: {\"application/octet-stream\"};\n" . " name=\"$files[$x]\"\n" .

          "Content-Disposition: attachment;\n" . " filename=\"$files[$x]\"\n" .

          "Content-Transfer-Encoding: base64\n\n" . $data . "\n\n";

          $message .= "--{$mime_boundary}\n";

      }

      // send

      $ok = @mail($to, $subject, $message, $headers);

      if ($ok) {

          echo "<p>mail sent to $to!</p>";

      } else {

          echo "<p>mail could not be sent!</p>";

      }

      ?>


```

Any thoughts would be brilliant!

-Ash R

---

### Post by ghostdog74 on 2008-10-30
this is working for 1 file
```

   $fileatt = "file"; // Path to the file
$fileatt_type = "application/octet-stream"; // File Type
$fileatt_name = "file"; // Filename that will be used for the file as the attachment

$email_from = "root@linux"; // Who the email is from
$email_subject = "test"; // The Subject of the email
$email_txt = "test"; // Message that the email has in it

$email_to = "somewhere@gmail.com"; // Who the email is too

$headers = "From: ".$email_from;

$file = fopen($fileatt,'rb');
$data = fread($file,filesize($fileatt));
fclose($file);

$semi_rand = md5(time());
$mime_boundary = "==Multipart_Boundary_x{$semi_rand}x";

$headers .= "\nMIME-Version: 1.0\n" .
"Content-Type: multipart/mixed;\n" .
" boundary=\"{$mime_boundary}\"";

$email_message .= "This is a multi-part message in MIME format.\n\n" .
"--{$mime_boundary}\n" .
"Content-Type:text/html; charset=\"iso-8859-1\"\n" .
"Content-Transfer-Encoding: 7bit\n\n" .
$email_message . "\n\n";

$data = chunk_split(base64_encode($data));

$email_message .= "--{$mime_boundary}\n" .
"Content-Type: {$fileatt_type};\n" .
" name=\"{$fileatt_name}\"\n" .
//"Content-Disposition: attachment;\n" .
//" filename=\"{$fileatt_name}\"\n" .
"Content-Transfer-Encoding: base64\n\n" .
$data . "\n\n" .
"--{$mime_boundary}--\n";

$ok = @mail($email_to, $email_subject, $email_message, $headers);

if($ok) {
echo "<font face=verdana size=2>The file was successfully sent!</font>";
} else {
die("Sorry but the email could not be sent. Please go back and try again!");
} 


```

make it into a function, then use a loop to go over your files in array, executing this function everytime.

---

### Post by s.fox on 2008-10-30
Hi,

Question: Would that not result in several emails being sent?

The only reason I ask is that I want to send all the files in a single email.  Having looked my code I suspect I am doing something wrong with the MIME encoding.

Thanks

-Ash R

---

### Post by ghostdog74 on 2008-10-30
```


$files = array("file","file2");
$to = "somewhere@gmail.com";
$from = "mail@mail.com";
$subject ="My subject";
$message = "My message";
$headers = "From: $from";
$semi_rand = md5(time());

$mime_boundary = "==Multipart_Boundary_x{$semi_rand}x";
$headers .= "\nMIME-Version: 1.0\n" . "Content-Type: multipart/mixed;\n" . " boundary=\"{$mime_boundary}\"";
$message = "This is a multi-part message in MIME format.\n\n" . "--{$mime_boundary}\n" . "Content-Type: text/plain; charset=\"iso-8859-1\"\n" . "Content-Transfer-Encoding: 7bit\n\n" . $message . "\n\n";

$message .= "--{$mime_boundary}\n";
for($x=0;$x<count($files);$x++){
    $file = fopen($files[$x],"rb");
    $data = fread($file,filesize($files[$x]));
    fclose($file);
    $data = chunk_split(base64_encode($data));
    $message .= "Content-Type: {\"application/octet-stream\"};\n" . " name=\"$files[$x]\"\n" .
    "Content-Disposition: attachment;\n" . " filename=\"$files[$x]\"\n" .
    "Content-Transfer-Encoding: base64\n\n" . $data . "\n\n";
    $message .= "--{$mime_boundary}\n";

}

 
$ok = @mail($to, $subject, $message, $headers);
if ($ok) {
    echo "<p>mail sent to $to!</p>";
} else {
    echo "<p>mail could not be sent!</p>";
}

```

---

### Post by s.fox on 2008-10-30
Hi,

Just had a thought that will sort of solve this problem.  I could just put all the files into a zip file and send that. :)

Yes,  its not the ideal way of doing it but it will work.  I would definately still like to get it to work the way i originally wanted to, so I could learn something.

Thanks

-Ash R

EDIT:  I was ninja'd! :)

Cool,  thanks for that.  Your script is working but its doing what my original script does.  It sends an email with no attachements.  I checked my file names and everything looks ok.  I have checked permissions (just in case)  and they also look ok.  Its most puzzling. 

Thank you for time and help ghost dog

---

### Post by ghostdog74 on 2008-10-30
well, it works for me.

---

