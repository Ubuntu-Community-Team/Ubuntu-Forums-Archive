---
title: "Subversion protocl ? RFC? web client..."
date: 2005-02-05
forum: Programming Talk
---

### Post by DarkSilver on 2005-02-05
Hello,
  
 I'm searching a web viewer for SubVersion in PHP
 Or making one myself
 
 The problem is there is no bindings for PHP (there are in python or perl, but not PHP)
 
 The only PHP client (websvn) uses system call to the command line client : svn
 (in order to work, it needs svn to be installed on the server, and a configuration of PHP that allows programs execution with the exec() or system() command and which has subversion installed, which it's not the case for every mutual web hosting servers..)
 
 A solution could be the use of a socket to communicate with subversion...
 
 But I didn't find any subversion protocol reference or RFC...
 How this protocol works?
 How can I code a SVN client ?
  There's nothing on the subversion website...
 
 Can you help me ?
 
 Thanks !

---

### Post by dataw0lf on 2005-02-05
Interesting idea.  Is [this](http://devel.akbkhome.com/svn/index.php/akpear/Stream_Subversion/Subversion.php)  what you're looking for ?
dataw0lf

---

### Post by DarkSilver on 2005-02-05
Thanks for the answer
     but no, it is not good...
     I explain :
     
      [PHP]
  function _svnExec($cmd,$url) {
   $svn  = trim(`which svn`);
   $url = escapeshellarg($url);
   //echo "\n$svn $cmd $url\n";
            
   $ph = popen("$svn  $cmd $url","r");
   $ret = '';
   while (!feof($ph)) {
 	$ret .= fgets($ph,1024) ;
   }   
   pclose($ph);
   //echo "GOT $ret";  
   return $ret;             
   }    [/PHP] 
    
     As you can see, it uses the svn command line client
     so, in order to work, it NEEDS the svn client to be installed !
     And it works only under Linux environment...
     
     The things I need is the SVN protocol in order to make it works with ONLY php !!!
     If I find this protocol, I can use a socket() to communicate with svn....

---

### Post by Nagol on 2005-05-04
I got exactly the same idea so i searched and found this one:

[http://svn.collab.net/repos/svn/trunk/subversion/libsvn_ra_svn/protocol](http://svn.collab.net/repos/svn/trunk/subversion/libsvn_ra_svn/protocol)

Maybe we could help each other to create a PHP class only using fsockopen and sockets functions

you can mail me to [email]nagol@erratum.net[/email]

---

