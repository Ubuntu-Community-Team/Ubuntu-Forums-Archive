---
title: "php and mysql pagination help"
date: 2008-01-11
forum: Programming Talk
---

### Post by greentiger on 2008-01-11
i'm a new-ish programmer to php and new to mysql (2 months) and i have a news publishing script. i got everything working just fine (display all entries, create, edit and drop news posts) but for the life of me i cannot figure out how to automatically paginate. i have tried several tutorials to no avail. i was wondering if i could paste my current page and see if there's anything anyone could suggest.

the code is from index-news.php which is an include to index.php. i have my urls look like this: [http://localhost/?a=&d=index-news.php](http://localhost/?a=&d=index-news.php).  $ _GET['d'] is got ( ;-) ) in index.php's body. 

```

	$hits = 4;

	// count how many rows there are
	require "./includes/dbconnect.$ext";
		$qstring = "SELECT newsid FROM news";
		$result = mysqli_query($dbconnect, $qstring) or die ('Could not retrieve news items');
		$count = mysqli_num_rows($result);
	require "./includes/dbclose.$ext";

	// spit out the range
	if($count)
		{
		require "./includes/dbconnect.$ext";
			// SQL statement from ars technica; the WHERE statement joins the two tables and correlates the two by way of X.userid
			$qstring = "SELECT news.newsid, users.username, news.title, news.newstext,
				DATE_FORMAT(news.postdate, '%M %D, %Y %l:%i %p') AS date, users.permissions
				FROM news, users WHERE news.userid = users.userid ORDER BY postdate DESC LIMIT $hits";
			$result = mysqli_query($dbconnect, $qstring) or die ('Could not retrieve news items');
		require "./includes/dbclose.$ext";

		require "./includes/f_advanced.$ext";

		while($row = mysqli_fetch_array($result))
			{
			// formatted values
			$news = nl2br(doBBCodes(strip_tags($row[3])));
			$imgname = pickAvatar($row[5]);

			print "	<table cellpadding=\"0\" cellspacing=\"0\" class=\"news_table\">\n";
			print "		<tr><td class=\"news_post_title\">\n";
			print "			<img src=\"./skin/$skinname/$imgname\" class=\"avatar\" alt=\"" . $row[1] . "'s avatar\">\n";
			print "			Subject: <strong>" . $row[2] . "</strong><br>\n<br>\n";
			print "			Posted by: " . ucfirst($row[1]) . "<br>\n";
			print "			Post date: " . $row[4] . "<br>\n";
			print "		<tr><td class=\"news_post_start\">&nbsp;</td></tr>\n";
			print "			<tr><td class=\"news_post_msg\"><p class=\"news_post_p\">\n";
			print "				$news\n";
			print "			</p></td></tr>\n";
			print "		<tr><td class=\"news_post_end\">&nbsp;</td></tr>\n";
			print "	</table>\n";
			print "<p>&nbsp;</p>\n";
			}
		}
	else
		{ print "There's no news today!"; }

```

EDIT: can any one help? or at least point me in the right direction?

---

### Post by bmeyer on 2008-02-15
This might be a little late, but here's a pagination function I use on a site.  It makes a pagination link system in the following form.:
|<     <<     1 2 3 4 5     >>     >|


```
function pagination($result_count){
	//$start is a variable in the URL --> ?start=_
	$start = $_GET['start'];;

	//remove start variable from URL -- to be replaced
	$url = preg_replace('/&start=(\d+)/', '', $_SERVER['REQUEST_URI']);
	$url = preg_replace('/start=(\d+)/', '', $url);
	//number of pages, 10 results per page
	$page_count = ceil($result_count / 10);
	
	//first page link
	$url_temp = preg_replace('/\?/', '?start=0&', $url);
	echo '<p>Page:&nbsp;&nbsp;&nbsp;<a href="'.$url_temp.'">|&lt;</a>&nbsp;&nbsp;&nbsp;';

	//if not first page, display link to previous page
	if ($start > 0){
		$previous_start = $start - 10;
		$url_temp = preg_replace('/\?/', '?start='.$previous_start.'&', $url);
		echo '<a href="'.$url_temp.'">&lt;&lt;</a>&nbsp;&nbsp;&nbsp;';
	}

	//display page number links
	for ($i = 0; $i < 10 * $page_count; $i=$i+10){
		$page = $i/10 + 1;
		if ($i == $start){
			$url_temp = preg_replace('/\?/', '?start='.$i.'&', $url);
			echo '<a href="'.$url_temp.'" class="bold">'.$page.'</a> ';
		}
		else {
			$url_temp = preg_replace('/\?/', '?start='.$i.'&', $url);
			echo '<a href="'.$url_temp.'">'.$page.'</a> ';
		}
	}

	//if not last page, display next page link
	if ($start < 10*($page_count-1)){
		$next_start = $start + 10;
		$url_temp = preg_replace('/\?/', '?start='.$next_start.'&', $url);
		echo '&nbsp;&nbsp;&nbsp;<a href="'.$url_temp.'">&gt;&gt;</a>';
	}

	//last page link
	$last_start = 10*($page_count-1);
	$url_temp = preg_replace('/\?/', '?start='.$last_start.'&', $url);
	echo '&nbsp;&nbsp;&nbsp;<a href="'.$url_temp.'">&gt;|</a></p>';
}
```

Then, to display the correct set of 10 results based on the current page (using the start variable in the URL), add this to your MySQL query:
```
"LIMIT ".$_GET['start'].", 10"
```

Hope it's not to late to help.  Feel free to contact me with questions.

---

### Post by greentiger on 2008-02-15
thank you for your reply. this is the code i'm currently using (it creates !<, < and >, >| links and displays a count of records).
i'm still learning so any input is helpful.

```

	// CREATE PREV LINKS 
	print "<div style=\"text-align: center;\">";

	/* if current record minus page hits makes the record index less than zero, set the record to 0 (the most recent);
	otherwise make the next record equal to current record - page hits */
	if (($record - $hits) < 0)
		{ $prev = 0; }
	else
		{ $prev = ($record - $hits); }

	/* if the record index is at 0 (the most recent row; due to reverse sorting) make a non-clicky link;
	otherwise there are still unviewed records and make a clicky link */
	if($record == 0)
		{ print "<img src=\"./images/nav/result_start.png\" alt=\"|<\" title=\"At most recent record\" border=\"0\">"; }
	else
		{
		print "<a href=\"./?a=$prev&d=index-news\">
			<img src=\"./images/nav/result_prev.png\" alt=\"<\" title=\"Previous records\" border=\"0\"></a>";
		}

	// TELL USER STATUS OF BROWSING 

	/* print intermediate text telling user their position in the records; if total records is less than hits, show end of table */
	if(($record + $hits) > $count)
		{ $showing = $count; }
	else
		{ $showing = ($record + $hits); }

	print " | Item(s) " . ($record + 1) . "-" . $showing . " of $count | ";

	// CREATE NEXT LINKS 

	/* if current index + hits would overshoot the last records then show the last $hits records;
	otherwise just go to the next set of X records starting at current record + hits */
	if (($record + $hits) > ($count - $hits))
		{ $next = ($count - $hits); }
	else
		{ $next = ($record + $hits); }

	/* if current index + hits would be over or equal to the number of items then disable clicky;
	otherwise enable the clicky */
	if (($record + $hits) >= $count)
		{ print "<img src=\"./images/nav/result_end.png\" alt=\">|\" title=\"At first record\" border=\"0\">"; }
	else
		{
		print "<a href=\"./?a=$next&d=index-news\">
			<img src=\"./images/nav/result_next.png\" alt=\">\" title=\"Next records\" border=\"0\"></a>";
		}

	print "</div><br>\n";

```

---

### Post by bmeyer on 2008-02-15
Is that working like you'd like it to, or is there something wrong or missing that you'd like added?

The URL of the site it's implemented on might help...

---

### Post by greentiger on 2008-02-15
there is no site yet that the project is running on (or at least not publicly accessible); i just wanted to post it here to see if there was something that was worth commenting on. the code works but i will also try your suggestion too to see how that works out.

---

