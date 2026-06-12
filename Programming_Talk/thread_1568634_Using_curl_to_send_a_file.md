---
title: "Using curl to send a file"
date: 2010-09-05
forum: Programming Talk
---

### Post by Paqman on 2010-09-05
I'm playing around with using curl to send a file to my server when a user runs a script.

I'm using curl in my bash script to send the file:
```
curl -F logfile=~/location/of/logfile http://myserver/target.php
```

The on the server I have the following PHP, which is supposed to write the posted file to target.txt:
```
<?php
//
// test page that accepts HTTP POST request only. for demo purpose
// accepts 'logfile' parameter, and records logfile and 
// browser user-agent to text files
// 


if (isset( $_POST['logfile'])) {
	
	$useragent = $_SERVER['HTTP_USER_AGENT'];
	$logfile=$_POST['logfile'];
	
	//log any post request to a textfile
	$fh = fopen("target.txt","a+");
	$text = "logfile : $logfile ($useragent)";
	$text.="\n";

	fputs($fh,$text);
	fclose($fh);

	// the positive response
	print "data was submitted successfully";

} else {
	// the negative response
	print "this page only accepts POST request";

}




?>
```

Can't get it to work though, i'm getting 500 Internal Server Error. I'm not really gripped up on PHP, I got target.php from [here]("http://linux.byexamples.com/archives/311/sending-http-post-using-curl-command/"), is this the problem?

---

### Post by James78 on 2010-09-05
Check the Apache error log, it should tell you what the problem is. It's been a lifesaver for me many times.

P.S. This might help you out.
[http://www.php-mysql-tutorial.com/wikis/php-tutorial/reading-a-remote-file-using-php.aspx](http://www.php-mysql-tutorial.com/wikis/php-tutorial/reading-a-remote-file-using-php.aspx)

---

