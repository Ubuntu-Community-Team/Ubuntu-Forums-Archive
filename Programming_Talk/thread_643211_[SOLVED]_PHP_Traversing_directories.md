---
title: "[SOLVED] PHP: Traversing directories"
date: 2007-12-17
forum: Programming Talk
---

### Post by x1a4 on 2007-12-17
Hi,

How do I traverse directories using PHP4?  I need to specify a directory and add all it's subdirectories (and their subdirectories etc) to an array, but have no idea how.  I know next to nothing about PHP.  Please help.  

Thank you.

---

### Post by KCPokes on 2007-12-17
Many different ways to do this, like anything else.  To make it simple, I'd use the glob() function:

```

foreach(glob('startDirectory/*.jpg') as $myFilename)
{
    echo 'Filename: ' . $myFilename . '<br />';
} 

```

In this case it would start in "startDirectory" and pull back everything, recursively, that is a *.jpg file.  There are options you can use to make the glob function more useful, such as providing multiple file types to match.  Search for glob() for more info.

---

### Post by x1a4 on 2007-12-17
Thanks for your reply but that's not what I'm looking for (my fault, I wasn't specific enough).  I need only the directories themselves and not their files.  

For example: 

assuming the following directory tree: 

mydir1/
-- sub1/
-- sub2/
mydir2/
-- sub1/
mydir3/
-- sub1/
---- sub1/
---- sub2/
-- sub2/
mydir4/
mydir5/

I want PHP to populate an array with something like this: 

myarray[0]=mydir1
myarray[1]=mydir1/sub1
myarray[2]=mydir1/sub2
myarray[3]=mydir2
myarray[4]=mydir2/sub1
myarray[5]=mydir3/
myarray[6]=mydir3/sub1
myarray[7]=mydir3/sub1/sub1
myarray[8]=mydir3/sub1/sub2
myarray[9]=mydir3/sub2
myarray[10]=mydir4
myarray[11]=mydir5

Would the following do the trick? 

```
foreach(glob('mydir1/') as $myarray) {
...
}
```

---

### Post by aks44 on 2007-12-17
See [is_dir]("http://fr2.php.net/manual/en/function.is-dir.php"), and:
- [scandir]("http://fr2.php.net/manual/en/function.scandir.php") if you're using PHP5
- [opendir]("http://fr2.php.net/manual/en/function.opendir.php"), [readdir]("http://fr2.php.net/manual/en/function.readdir.php"), [closedir]("http://fr2.php.net/manual/en/function.closedir.php") if you're using PHP4

In both cases iterate on the contents of the directory, check with **is_dir** and don't forget to take **.** and **..** into account.

---

### Post by KCPokes on 2007-12-17
I'm just doing this in my head, as I'm at work and really no place to try it out...

```

foreach(glob('startDirectory/*', GLOB_ONLYDIR) as $myFilename)
{
    echo 'Filename: ' . $myFilename . '<br />';
}

```

Try that.

---

### Post by x1a4 on 2007-12-17
Will this do the trick? 

```

$startdir=$_SERVER[DOCUMENT_ROOT]."/mydir1/";
$i=0;
  
if($handle=opendir($startdir)) {
  while(($file=readdir($handle))!==false) {
    if(is_dir($file) && ($file!=".") && ($file!="..")) {
      $dirs=array($i=>$file);
      $i++;
    }
  }
  closedir($handle);
}

```

---

### Post by x1a4 on 2007-12-17
> **KCPokes said:**
> I'm just doing this in my head, as I'm at work and really no place to try it out...

```

foreach(glob('startDirectory/*', GLOB_ONLYDIR) as $myFilename)
{
    echo 'Filename: ' . $myFilename . '<br />';
}

```

Try that.

It only gives me directories in startDirectory/ but not their subdirectories.

---

### Post by KCPokes on 2007-12-17
Just tested and this works, including a trailing slash for the directories.  You can remove the slash if you don't want it.

```

<?php

foreach(glob('/export/home/*',GLOB_ONLYDIR | GLOB_MARK) as $myFilename)
{
   echo "Directory: ".$myFilename."\n";
}
?>

```

Goes back to there being multiple ways of doing this.

---

### Post by KCPokes on 2007-12-17
> **x1a4 said:**
> It only gives me directories in startDirectory/ but not their subdirectories.

Ahh, you are correct.  Nevermind then....where I was testing didn't go deep enough.

---

### Post by KCPokes on 2007-12-17
Threw it together real quick, making it a function that you'd call from another script, but this works:

```

<?php

recurse('/tools/www');

function recurse($path)
{
  foreach(glob($path."/*",GLOB_ONLYDIR) as $myDirectory)
  {
      echo "Directory :".$myDirectory."\n";
      recurse($myDirectory);
  }
}
?>

```

Watch your trailing slash in the directory you pass, as it is not needed.

---

### Post by aks44 on 2007-12-17
> **x1a4 said:**
> ```
$startdir=$_SERVER[DOCUMENT_ROOT]."/mydir1/";
$dirs=array();
$i=0;
  
if($handle=opendir($startdir)) {
  while(($file=readdir($handle))!==false) {
    if(is_dir($file) && ($file!=".") && ($file!="..")) {
      $dirs[$i]=$file;
    }
    $i++;
  }
  closedir($handle);
}
```

Your code will work for **one directory level**. If you want to achieve what you stated before, better wrap it inside a function, and make it recursive. From the top of my head:

[php]function scan_dir_tree($basedir, $appenddir = '', $dirs = array())
{
  if (($handle = opendir($basedir)) !== false)
  {
    while (($file = readdir($handle)) !== false)
    {
      if(is_dir($basedir.'/'.$appenddir.$file) && ($file != '.') && ($file != '..'))
      {
        $dirs[] = $appenddir.$file;
        $dirs = scan_dir_tree($basedir, $appenddir.$file.'/', $dirs);
      }
    }
    closedir($handle);
  }
  return $dirs;
}

$dirs = scan_dir_tree($_SERVER[DOCUMENT_ROOT].'/mydir1');[/php]


I've not tested it but it should work (more or less) as expected.

NOTE: if you don't provide the trailing **/** in the **$basedir** argument, the **'/'** is needed in the **is_dir** line. However if you do provide the **/** in the **$basedir** argument then remove it from the **is_dir** line.


Oh well, I just saw the **glob** documentation, it indeed looks way easier to use. Anyway you can still merge both my example and KCPokes' one so that you have a recursive glob that actually returns an array... ;)

---

### Post by x1a4 on 2007-12-17
Thank you both.  Here's how I got it to work: 
```

function recurse($path,$dirs=array()) {
  foreach(glob($path."/*",GLOB_ONLYDIR) as $d) {
    $GLOBALS['dirs'][]=$d;
    recurse($d,$dirs);
  }
}
  
$dirs=array();
recurse($_SERVER[DOCUMENT_ROOT]."/path");
// now I have a $dirs array containing all the directories in $path

```

---

