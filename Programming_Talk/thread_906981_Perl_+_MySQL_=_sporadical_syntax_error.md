---
title: "Perl + MySQL = sporadical syntax error"
date: 2008-09-01
forum: Programming Talk
---

### Post by osjak on 2008-09-01
Hi All,

I am very new to Perl and trying to practice a bit. I am rebuilding my website and decided to take on a project - convert an Simple Machine Forum database into vBulletin database. At the present stage my script successfully converts user and topic tables, but I am stuck on converting post table. When I run the script, it converts about a hundred of posts and then throws an SQL syntax error. What is puzzling is why this *syntax error comes up after multiple executions of the query*? Here is the post converting portion of my script:

```
# Transfer all messages from SMF to VB. Usage: transfer_messages ()
sub transfer_messages {

	# Rotate through user database - read old SMF database, create new userid and insert new record into vBulletin database
	my $sql_smf_post;
	my $sth_smf;
	my @row_post; # This will be a placeholder for our results
	my $sql_new_post;
	my $sth_vb;
	my %new_post = (
			'postid', 0,
			'threadid', 0,
			'parentid', 0,
			'username', '',
			'userid', 0,
			'title', '',
			'dateline', 0,
			'pagetext', '',
			'allowsmilie', 1,
			'showsignature', 0,
			'ipaddress', '',
			'iconid', 0,
			'visible', 1,
			'attach', 0,
			'infraction', 0,
			'reportthreadid', 0,
			'ame_flag', 0,
			'nominate_topic_amount', 0,
			'nominate_topic_award', 0,
			'nominate_topic_award_rank', 0,
			'post_thanks_amount', 0
	);

	
	#################
	# Pull data from the post
	$sql_smf_post = qq{SELECT ID_MSG, ID_TOPIC, ID_MEMBER, subject, posterTime, body, posterIP FROM ${smf_db_prefix}messages WHERE $topic_id_range ORDER BY ID_MSG};
	$sth_smf = $dbh_smf->prepare($sql_smf_post);
	$sth_smf->execute or die("\nSQL error in loop1 ! $DBI::errstr");
	
	while (@row_post = $sth_smf->fetchrow_array) {  # retrieve one row
		# Set new post values
		$new_post{'postid'} = get_postID ($row_post[0]);
		$new_post{'threadid'} = get_topicID ($row_post[1]);
		$new_post{'parentid'} = get_parentID ($row_post[0], $row_post[1]);
		$new_post{'username'} = convert_userName ($row_post[2]);
		$new_post{'userid'} = convert_userID ($row_post[2]);
		$new_post{'title'} = Convert::Cyrillic::cstocs ($encode_src, $encode_dst, $row_post[3]);
		$new_post{'dateline'} = $row_post[4];
		$new_post{'pagetext'} = Convert::Cyrillic::cstocs ($encode_src, $encode_dst, $row_post[5]);
		$new_post{'ipaddress'} = $row_post[6];
		$new_post{'attach'} = count_post_attachments ($row_post[0]);
		
		#################
		# Write new post row to VB database
		$sql_new_post = "INSERT INTO " . ${vb_db_prefix} . "post VALUES (
			'" . $new_post{'postid'} . "', '" .
			$new_post{'threadid'} . "', '" .
			$new_post{'parentid'} . "', '" .
			$new_post{'username'} . "', '" .
			$new_post{'userid'} . "', '" .
			$new_post{'title'} . "', '" .
			$new_post{'dateline'} . "', '" .
			$new_post{'pagetext'} . "', '" .
			$new_post{'allowsmilie'} . "', '" .
			$new_post{'showsignature'} . "', '" .
			$new_post{'ipaddress'} . "', '" .
			$new_post{'iconid'} . "', '" .
			$new_post{'visible'} . "', '" .
			$new_post{'attach'} . "', '" .
			$new_post{'infraction'} . "', '" .
			$new_post{'reportthreadid'} . "', '" .
			$new_post{'ame_flag'} . "', '" .
			$new_post{'nominate_topic_amount'} . "', '" .
			$new_post{'nominate_topic_award'} . "', '" .
			$new_post{'nominate_topic_award_rank'} . "', '" .
			$new_post{'post_thanks_amount'} . "'
		)";
		
 		$sth_vb = $dbh_vb->prepare($sql_new_post);
		$sth_vb->execute or die("\nError executing SQL statement! $DBI::errstr");
		
		
	}
}

```

And here is the error that I get:

> Error executing SQL statement! You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '1', '0', '555.555.55.555', '0', '1', '0', '0', '0', '0', '0', '0', '0', '0'
)' at line 2 at ./rw_data_swap.pl line 537.

Could anyobe tell me what could cause this error? Could it be my script running out of memory? I'm using an old beater machine with 256MB for this project.

---

### Post by odyniec on 2008-09-01
It seems it encounters a problem with the "pagetext" field -- I suspect there might be some character in the text that breaks the SQL query (for example, a single quote character which normally indicates the end of text data).

Try escaping the textual data and see if it solves the problem -- see this part of DBI documentation for more info: [http://search.cpan.org/~timb/DBI-1.607/DBI.pm#quote](http://search.cpan.org/~timb/DBI-1.607/DBI.pm#quote).

---

### Post by osjak on 2008-09-01
> **odyniec said:**
> 
Try escaping the textual data and see if it solves the problem -- see this part of DBI documentation for more info: [http://search.cpan.org/~timb/DBI-1.607/DBI.pm#quote](http://search.cpan.org/~timb/DBI-1.607/DBI.pm#quote).
odyniec, thank you for your advice! Being very new to Perl (and programming all together) I have tried searching for answers everywhere but in the DBI library manual. I see now that I really need to read through it to understand better what I am working with and what options I have. While waiting for responses I decided to re-setup my little development server, so I am down for several hours. I will read that manual and try to implement your advice as soon as I can and will report back here.

---

### Post by osjak on 2008-11-02
odyniec, your advice certainly helped. All I had to do was to use the built-in quoting function like this:
```
$dbh_vb->quote($new_post{'pagetext'})
```
Thanks again.

---

