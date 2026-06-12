---
title: "PHProblems."
date: 2010-01-10
forum: Programming Talk
---

### Post by Godd on 2010-01-10
I'm designing a commenting system for my website, and I'm getting 
[I]
Parse error: syntax error, unexpected '}'[/I]

I've checked to see if all the curly brackets have a beginning and end. And they do. This would mean, to me, that there is something before the error that is making it seem as though the bracket is improperly placed. But as far as I can tell, the syntax for everything prior to it is peachy keen. But obviously, I have to be wrong in one of those assumptions. Ha.

[PHP]	if(!in_array($current_comm_array['cid'], $com_seq)){ 

#Not_r $$ no_r	if($current_comm_array['cidr'] == "0" && $reply_commen_array['cidr'] != $current_comm_array['cid']){ 

#adds to sequence       $seq_tmp = array( $next => $current_comm_array['cid'] ); 
               	                    $com_seq = array_merge($com_seq, $seq_tmp); 
	 
                        	    echo $main_cycle . "1"; 

		     $next++; 
		     $main_cycle++;                                   } 
							 
#Not_r $$ y_r	elseif($current_comm_array['cidr'] == "0" && $reply_commen_array['cidr'] == $current_comm_array['cid']){ 
	 
#adds to sequence       $seq_tmp = array( $next => $current_comm_array['cid'] ); 
                                    $com_seq = array_merge($com_seq, $seq_tmp); 

                                    $next++; 
		    $main_cycle = $reply_commen_array['cid']; 

#adds new tab lvl	$tab_tmp = array( $next_tab => $current_comm_array['cid'] ); 
		$tab_lvl = array_merge($tab_lvl, $tab_tmp); 
                                $next_tab++; 

#sets tab level 	$tab = end($tab_lvl); 

									   } 

#R $$ no_r	elseif($current_comm_array['cidr'] != "0" && $reply_commen_array['cidr'] != $current_comm_array['cid']){ 
 
#adds to sequence       $seq_tmp = array( $next => current_comm_array['cid'] ); 
                        $com_seq = array_merge($com_seq, $seq_tmp); 

                        $next++; 

		        $next_reply = mysql_fetch_array($reply_commen); 
				 
#chks if last reply	if(!$next_reply){ 

				$tab = prev($tab_lvl); 
				$main_cycle = $tab; 

					} 

			elseif($next_reply){ 

				$main_cycle = $next_reply['cid']; 
		 
					   } 
								} <= ERROR
		 
#R && y_r	elseif($current_comm_array['cidr'] != "0" && $reply_commen_array['cidr'] == $current_comm_array['cid']){	 

#adds to sequence       $seq_tmp = array( $next => $current_comm_array['cid'] ); 
                        $com_seq = array_merge($com_seq, $seq_tmp); 

                        $next++; 

                        $main_cycle = $reply_commen_array['cid']; 

#adds a new tab lvl     $tab_tmp = array( $next_tab => $current_comm_array['cid'] ); 
                                    $tab_lvl = array_merge($tab_lvl, $tab_tmp); 
                                    $next_tab++; 

		     $tab = end($tab_lvl); 

									   } 
	
						} 
[/PHP]

I directly noted the location of the error.

---

### Post by Hellkeepa on 2010-01-10
HELLo!

Please, please! Use proper indenting. If you had, catching this issue would have been trivial.
Also, newlines aren't trivial either... Read the code above, to see what I mean.

Happy codin'!

---

### Post by Godd on 2010-01-10
Ha, The indenting was lost in the transfer from the terminal to the page. I didn't know that the newlines mattered in PHP, so I'll fix that and see if it helps. The code that's in use has proper indentation.

[PHP]    if(!in_array($current_comm_array['cid'], $com_seq)){ 

#Not_r $$ no_r    if($current_comm_array['cidr'] == "0" && $reply_commen_array['cidr'] != $current_comm_array['cid']){ 

#adds to sequence       $seq_tmp = array( $next => $current_comm_array['cid'] ); 
                        $com_seq = array_merge($com_seq, $seq_tmp); 
     
                        echo $main_cycle . "1"; 

                        $next++; 
                        $main_cycle++;} 
                             
#Not_r $$ y_r    elseif($current_comm_array['cidr'] == "0" && $reply_commen_array['cidr'] == $current_comm_array['cid']){ 
     
#adds to sequence       $seq_tmp = array( $next => $current_comm_array['cid'] ); 
                        $com_seq = array_merge($com_seq, $seq_tmp); 

                        $next++; 
                        $main_cycle = $reply_commen_array['cid']; 

#adds new tab lvl       $tab_tmp = array( $next_tab => $current_comm_array['cid'] ); 
                        $tab_lvl = array_merge($tab_lvl, $tab_tmp); 
                        $next_tab++; 

#sets tab level         $tab = end($tab_lvl);} 

#R $$ no_r    elseif($current_comm_array['cidr'] != "0" && $reply_commen_array['cidr'] != $current_comm_array['cid']){ 
 
#adds to sequence       $seq_tmp = array( $next => current_comm_array['cid'] ); 
                        $com_seq = array_merge($com_seq, $seq_tmp); 
                        $next++; 

                        $next_reply = mysql_fetch_array($reply_commen); 
                 
#chks if last reply    if(!$next_reply){ 

                               $tab = prev($tab_lvl); 
                               $main_cycle = $tab;} 

                       elseif($next_reply){ 

                               $main_cycle = $next_reply['cid']; 
         
                       } 
                                } <= ERROR
         
#R && y_r    elseif($current_comm_array['cidr'] != "0" && $reply_commen_array['cidr'] == $current_comm_array['cid']){     

#adds to sequence       $seq_tmp = array( $next => $current_comm_array['cid'] ); 
                        $com_seq = array_merge($com_seq, $seq_tmp); 

                        $next++; 

                        $main_cycle = $reply_commen_array['cid']; 

#adds a new tab lvl     $tab_tmp = array( $next_tab => $current_comm_array['cid'] ); 
                        $tab_lvl = array_merge($tab_lvl, $tab_tmp); 
                        $next_tab++; 

                        $tab = end($tab_lvl); 

                                       } 
    
                        }  [/PHP]

EDIT: Hopefully that remediated the tabs.

---

### Post by Hellkeepa on 2010-01-10
HELLo!

Normally they don't, no. For line-based commenting, however...

Happy codin'!

---

### Post by qalimas on 2010-01-10
If that is how it looks in your editor, you have a few problems.  You can't put code on the same lines as comments (lines starting with #) if you want the comment to come first.

Also, PHP will usually give you a line number, or an excerpt from around where it had the error, could you post that?

---

### Post by Hellkeepa on 2010-01-10
HELLo!

He marked the line with a comment, which wasn't a comment. More specifically, this part "<= ERROR".
Though, as you also pointed out: This isn't the actual error, just a symptom of it.

Happy codin'!

---

### Post by wmcbrine on 2010-01-10
Dude, I know nothing about PHP, and even I can see what's wrong with this code. Just look at the syntax highlighting that vBulletin does for you -- all those yellow lines are where your code is *commented out* -- almost half of it!

"#" starts a comment, and a newline finishes it. Surely you realize there has to be a comment terminator of some kind? And you know it's not a space, because you have spaces in your (intended) comments. Well, a tab doesn't do it, either -- only a newline.

---

### Post by qalimas on 2010-01-10
Sorry, didn't notice that :popcorn:

Anyway, I tidied it up some, see attachment.

After properly aligning and removing comments, I don't see anything wrong with the braces, but I could be overlooking something.

---

### Post by Hellkeepa on 2010-01-10
HELLo!

There's nothing wrong the braces. As I tried to hint at, and both **wmcbrine** and **qualimas** stated directly: It was your comments. To be more specific, when you start a comment with # (or //), it lasts until the end of line. End of line is signalled with a newline.

You do have another problem though, on line 19 of the code you posted last. Which is in the original code as well.

Happy codin'!

---

### Post by wmcbrine on 2010-01-10
I don't think there *is* a problem with the braces, except that a bunch of them are commented out. If you count the nesting level, starting at zero, and including the commenting as shown, the indicated error line is where the level hits -2. This might reflect another "{" at the beginning that's not reproduced here.

If the lines with brackets are uncommented, the level count never goes negative.

Edit: Ah, Hellkeepa posted while I was typing.

---

