---
title: "Python, information between two tags"
date: 2007-03-07
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-07
Hi, I'm trying to make a Python script that connects to a forum's 'New Post' feature and prints the new posts... However, I've ran into a small problem. I'm not sure how to search for the information between the two tags.

So, I've got my script to connect to the website and get the sourcecode, but yeah... I'm trying to get the infromation between <table class='ipbtable' cellspacing="1"> and <!-- END RESULTS TABLE -->

I then want to get information from each little table that holds the new posts topic (Which happens to be the link), who the creator of the thread is and what thread it is in. So, I'm just wonder how in the world I'd do that.

This is the html that holds all the information I want (For just one topic):

```
<!-- Begin Topic Entry 4698 -->
	<tr>
		<td align="center" class="row2"><img src='style_images/poison[1]/f_norm.gif' border='0'  alt='New Posts' /></td>
		<td align="center" width="3%" class="row1">&nbsp;</td>
		<td class="row2">

			<table class='ipbtable' cellspacing="0">
				<tr><td valign="middle"><a href='http://cruels.net/index.php?showtopic=4698&amp;view=getnewpost'><img src='style_images/poison[1]/newpost.gif' border='0'  alt='Goto last unread' title='Goto last unread' hspace=2></a></td>					<td width="100%"> <a href="http://cruels.net/index.php?showtopic=4698&amp;hl=">Who loves the Chocolate?</a>  </td>
				</tr>
			</table>
			<span class="desc">Everybody loves the chocolate!</span>
		</td>

		<td class="row2" width="15%"><span class="forumdesc"><a href="http://cruels.net/index.php?showforum=43" title="Funny Stuff">Funny Stuff</a></span></td>
		<td align="center" class="row1"><a href='http://cruels.net/index.php?showuser=435'>Lovh0</a></td>
		<td align="center" class="row2"><a href="javascript:who_posted(4698);">3</a></td>
		<td align="center" class="row1">25</td>
		<td class="row1"><span class="desc">Today, 07:27 AM<br /><a href="http://cruels.net/index.php?showtopic=4698&amp;view=getlastpost">Last post by:</a> <b><a href='http://cruels.net/index.php?showuser=32'>Jazz00006</a></b></span></td>

	</tr>
<!-- End Topic Entry 4698 --><
```

So, if anyone can tell me how to get that needed information, from each new post I'd be much appreciated. Or, better yet, tell me where I can get the information to do it so I can learn how to do it myself... If you understand me. 

Thanks for any and all help.

---

### Post by ghostdog74 on 2007-03-07
for parsing HTML, you can try [BeautifulSoup/]("http://www.crummy.com/software/BeautifulSoup/"). Or search google for "Python HTML parsers". Or by hand, you can use regular expression. By the way, i can't find 
<table class='ipbtable' cellspacing="1"> and
<!-- END RESULTS TABLE --> in your example.

---

### Post by Darkness3477 on 2007-03-07
Oh, I should have added... That's just one part of the stuff I want to get... A hole bunch of them is contained between those two tags... I'll look into that stuff now. Thanks...

---

