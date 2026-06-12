---
title: "php is_dir function not working on ntfs mounted volume"
date: 2010-03-06
forum: Programming Talk
---

### Post by ernest_francis on 2010-03-06
have a normal ntfs volume, trying to test if a given path is a directory, which it is and it's failing, no error messages just not working

running latest php + apache2  with a virtual host environment 

any ideas folks, thanks

Ernest

---

### Post by Hellkeepa on 2010-03-06
HELLo!

Can you give us an example of the code that's failing?
Also, make sure that the path is absolutely correct. Do keep in mind that the CWD for a PHP script is the same as the landing file, even if the included files are stored in other folders.

Happy codin'!

---

### Post by ernest_francis on 2010-03-06
I am not changing directory, the function is below.

This is odd because when I pass it say the path "/media/offline1/stuff/" it works (its a external hd , ext3 format, but when i pass it "/media/offline2/stuff" which is a ntfs mount it falls over.... any ideas ?

$tree is glob array defined originally as $tree = array(); no problem there, i dont think it is a coding issue, more a permission/rights issue

function gettree($dir){
   global $tree;
   $tree[] = $dir;

   if (is_dir($dir)) {
 
      if ($dh = opendir($dir)) {

         while (($file = readdir($dh)) !== false) { 
            $full_name = $dir . $file;
            if ( $file[0] != '.' AND is_dir($full_name) and (array_search($full_name, $tree) === false) ) {
               gettree( ($full_name . "/") );}} 
         closedir($dh);}} 
    return ;}

---

