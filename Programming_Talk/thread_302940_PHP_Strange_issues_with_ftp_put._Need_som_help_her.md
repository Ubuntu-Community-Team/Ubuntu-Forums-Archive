---
title: "PHP: Strange issues with ftp_put. Need som help here.."
date: 2006-11-19
forum: Programming Talk
---

### Post by haaglin on 2006-11-19
Hi.

I'm developing an auto installer for my CMS system. The installer unpacks a zip file with the files, that i transfered to the server. And to get around permission issues, i unpacked the files into a temp dir, and i'm trying to move everything inside the temp dir, back to root with php's ftp functions. then delete the temp folder. 

My problem is that it only transfer a small amount of the files. i have tried the "set_time_limit(0);", but still only a few files get transfered, and i get no errors. I have narrowed it down to the ftp_put command, because making the folders works just fine. On my own server (php 5) , this works fine, but not on a server with php 4. If that makes a difference. Here is the script:

```
<?php
set_time_limit(0);
function getmode($file) {
	$ascii = array('.asp$','.bat$','.c$','.cgi$','.cpp$','.css$','.dhtml$','.diz$','.h$','.htm$','.html$','.ini$','.mak$','.nfo$','.pas$','.php$','.php3$','.pl$','.sfv$','.shtm$','.shtml$','.tcl$','.txt$');
	foreach($ascii as $ext) {
		if (eregi($ext, $file)) {
			return FTP_ASCII;
		}
	}
	return FTP_BINARY;
}
function move_recursive($from,$to) {
        global $conn_id;
	$to = str_replace("//","/",$to);
	$current_dir = opendir($from);
	while (false !== ($dir = readdir($current_dir))) {
		if ($dir !== '.' && $dir !== '..') {
			if(is_dir($from .'/'. $dir)) {
			       ftp_mkdir($conn_id, str_replace("//","/",$to ."/". $dir ."/"));
                               if(!move_recursive($from .'/'. $dir,$to .'/'. $dir)) {
						return false;
				}
			}
			else {
				
				$source = $from ."/". $dir;
				$dest = str_replace($_SERVER['DOCUMENT_ROOT'],"",$to ."/". $dir);
				$dest = str_replace("//","/",$dest);
				if(file_exists(str_replace("//","/",dirname($_SERVER['DOCUMENT_ROOT'].$dest)))) {
					ftp_put($conn_id, $dest ,$source, getmode($source));
				}
			}
		}
	}
	closedir($current_dir);
	return true;
}
$ftp_server= "localhost";
$ftp_user = "****";
$ftp_pass = "****";
$conn_id = ftp_connect($ftp_server); 
if (!ftp_login($conn_id, $ftp_user, $ftp_pass)) {
   	echo 'Connection failed.<br>';
	exit;
}
if(move_recursive(realpath("../temp"),"/")) {
	echo "Finished.";
}
ftp_close($conn_id);
?>
```

---

### Post by haaglin on 2006-11-20
*bump*

---

### Post by haaglin on 2006-11-21
This is the last entry in the pure-ftp log:

> Nov 20 01:57:03 server10 pure-ftpd: (******@localhost) [NOTICE] *path to file* uploaded  (1461 bytes, 7505.88KB/sec)
Nov 20 01:57:03 server10 pure-ftpd: (******@localhost) [NOTICE] *path to file* uploaded  (3945 bytes, 12553.86KB/sec)
Nov 20 02:12:03 server10 pure-ftpd: (******@localhost) [INFO] Timeout - try typing a little faster next time
Nov 20 02:28:58 server10 pure-ftpd: (******@******) [INFO] Timeout (no operation for 1800 seconds) 

I have searched everywhere for an answer, but it seems as if i am the only one with this problem?

---

