---
title: "Special char of page break in pdftotext."
date: 2013-01-15
forum: New to Ubuntu
---

### Post by lordius1990 on 2013-01-15
Hello all, I'm new new in ubuntu. I've a simple task parse pdf in php, I've already convert in to text by pdf to text but I need to know a code of page break char in pdftotext inserts. 
My idea(php code):

  $file = file_get_contents('./1.txt', FILE_USE_INCLUDE_PATH);
     $filearray = explode("page_break_char", $file);

    while (list($var, $val) = each($filearray)) {
        ++$var;
        $val = trim($val);
        echo "<pre>";
        print "Line $var: $val<br />";
         echo "</pre>";
    }

---

### Post by squakie on 2013-01-15
Why not create a simple 2-page document, like the following, output as PDF, then run back through the PDF to Text conversion and dump the file?

test page 1
<page break>
test page 2

---

### Post by lordius1990 on 2013-01-15
Unforchantly I can parse good text in php, I need to know what page I am in pdf. About lines I can use 
$file = file_get_contents('./1.txt', FILE_USE_INCLUDE_PATH);
    echo "<pre>";
   // echo $file;
    echo "</pre>";
     $filearray = explode("\n", $file);

    while (list($var, $val) = each($filearray)) {
        ++$var;
        $val = trim($val);
        echo "<pre>";
        print "Line $var: $val<br />";
         echo "</pre>";
    }
where "\n" is special char of new line.
Sorry for bad English.

---

### Post by lordius1990 on 2013-01-15
I use this command for convert pdftotext -layout [PDF-file [text-file]]

---

### Post by lordius1990 on 2013-01-15
Ok, try edit in windows by notepad++ end find end replace a page break lines(emty lines between pages after converting) to own symbol. Great thanks for all.

---

