---
title: "hello, today we will know how to know the content of any folder with the php with a s"
date: 2010-05-30
forum: Programming Talk
---

### Post by astkboy2008 on 2010-05-30
hello,
today we will know how to know the content of any folder with the php with a simple code
first you should [download this simple class]("http://www.jooria.com/projects/view?project=989&m=downloads")

then we can use it for that
just include it
[PHP]require_once ('readDir.class.php');[/PHP] and start new one
then you have to set the path of your folder
[PHP]if (!$dir->setPath( $base_dir.'/example' )) {
    die($dir->error());
} [/PHP]
know if you want to make the system going on any sub folder just use
[PHP]$dir->readRecursive(true);[/PHP]
and you can use the call back system in the class just like that
[PHP]// set a function to call when a new dir is read
if (!$dir->setEvent( 'readDir_dir', 'my_dir_function' )) { ;
    die($dir->error());
} 
// set a function to call when a new file is read
if (!$dir->setEvent( 'readDir_file', 'my_file_function' )) {
    die($dir->error());
} 
[/PHP]
you can see the example:[example.php]("http://www.jooria.com/view/file/511/example.php")
and you can make the system stoping at a specifice point just like that
[PHP]    if ($filename == 'secret_php_file.php') {
        echo 'We found the file we are looking for. Stopping directory read.<br />';

        return -1; // return negative 1 to stop the reading of the directory
    }
[/PHP]

---

