---
title: "Converter po =&gt; mo in php"
date: 2010-07-19
forum: Programming Talk
---

### Post by januzi on 2010-07-19
Hi

I'm looking for the php script that will create *.mo files. Google didn't help.

---

### Post by Xyro on 2010-07-19
[PHP]
  1 <?php
  2 
  3 $fp = fopen('mo_file.mo','w');
  4 fprintf( $fp, "I am a *.mo file." );
  5 fclose($fp);
  6 
  7 ?>
[/PHP]
Is that what you wanted? If not, you're going to have to be quite a bit more specific.

---

### Post by januzi on 2010-07-19
Mo file format: [http://www.gnu.org/software/hello/manual/gettext/MO-Files.html](http://www.gnu.org/software/hello/manual/gettext/MO-Files.html)

---

### Post by soltanis on 2010-07-19
Still not specific enough. From what I gathered on what you gave us, .MO files have something to do with the gettext utilities, but you still have yet to tell us what you are trying to accomplish or why you need to be writing these files in the first place.

---

### Post by Xyro on 2010-07-19
This might be of use to you: [http://pear.php.net/package/File_Gettext]("http://pear.php.net/package/File_Gettext/redirected")

I wont be able to help you with it further, as before today I'd never heard of *.mo, *.po or gettext.

Note: The second hit on the Google search "[php mo to po]("http://www.google.ca/#hl=en&q=php+mo+to+po&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=54f568e758bc4ec4")" lead me to this... Although, this thread is now #6, so there are slim pickin's for that query :P

For future reference, [this link might be helpful]("http://www.linuxquestions.org/linux/answers/LinuxQuestions_org/How_To_Ask_a_Question").

---

