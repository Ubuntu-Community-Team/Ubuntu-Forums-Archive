---
title: "Php stored procedure help"
date: 2009-01-02
forum: Programming Talk
---

### Post by tmatt95 on 2009-01-02
Hi I am writing a php script for for my website to access a database. I can run one stored procedure alright, however when I try and run two the second does not want to run. I inserted some debugging code and it prints "failed 2" onto the screen even though the sql code will run in the mysql query browser. Below is the code I am trying to get to work:

[PHP]$dblatestimage2 ="CALL bw_ProfileGetLatestUploadedImage(1)";
 	/*calls random image */
	$latestimage2 = $db->query($dblatestimage2); 
	if ($latestimage2 == FALSE) {
		print "failed1";
		exit;
	}
 	$row2 = $latestimage2->fetch_assoc();


	$dblatestimage3 ="CALL bw_ProfileUserIDGet('administrator')";
 	/*calls random image */
	$latestimage3 = $db->query($dblatestimage3); 
	if ($latestimage3 == FALSE) {
		print "failed2";
		exit;
	}
 	$row3 = $latestimage3->fetch_assoc();[/PHP]

I get a  "Call to a member function fetch_assoc() on a non-object"

Can anyone help remove the error. 

Thanks,

Matt

---

