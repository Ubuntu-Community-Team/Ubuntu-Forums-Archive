---
title: "[php] problems looping through an array"
date: 2009-07-03
forum: Programming Talk
---

### Post by ELD on 2009-07-03
Hi all currently i am looping through sql and setting the findings into an array and then later using a foreach loop to output what it has.

It nearly works but a major problem is that it seems to double up sometimes with the wrong info?

This is how i set the array:
[php]
while ($get_posts = $db->fetch_array($pagination_query))
{
    $this->post_array[] = $get_posts;
}
[/php]

Then i loop through it later on using this:
[php]
foreach ($this->post_array as $post)
[/php]

I need to do it like this as i get other information and echo out before the loop is done like so:

(this sets the title in the header of the document from the array gathered ealier)
[php]
$title_header = " >> {$lang['viewtopic']} >> {$this->post_array[0]['title']}";
[/php]

I know i am probably making some stupid mistake?

You can see how annoying the error is here:
[http://www.prxa.info/forum/viewtopic.php?tid=97](http://www.prxa.info/forum/viewtopic.php?tid=97)
(as you can see there it shows the first one fine but then makes me have a reply for each other persons reply lol).

---

### Post by smartbei on 2009-07-03
EDIT: See bottom of post.

I am not sure what your db object does, but if it works like mysql_fetch_array, then you are actually getting two versions of every row - one where the indices are numbers, and the other where they are strings that are the names of the columns. For it to work as you want, you probably need either:
[php]
$get_posts = $db->fetch_array($pagination_query)
// which returns only numbers-based arrays.
[/php]
or:
[php]
$get_posts = $db->fetch_assoc($pagination_query)
// which returns only names-based arrays.
[/php]
Instead. Otherwise, you can also pass an argument to mysql_fetch_array that will tell it to only return the type you want. See [http://il.php.net/mysql_fetch_array](http://il.php.net/mysql_fetch_array)

EDIT: I believe that I have been mistaken - at first glance I didn't understand the problem you have right. My solution doesn't seem relevant.

---

### Post by cpetercarter on 2009-07-03
I think you need to do a bit more work yourself to identify where the problem arises - is it when you first create the array; or is it later when you try to loop through it.

Can you not print out the array, using print_r ($array_name), after you have created it; to check that it actually contains the data you expect. If it doesn't, then the problem may lie in the coding for $pagination_query.

If the problem isn't there, it would be helpful if you could post the details of the foreach loop, since it may be there that the error occures.

---

### Post by ELD on 2009-07-03
It is nothing to do with the query while i would love it to be that simple heh. I did try it and i think i will start using fetch_assoc in a lot of areas, since theres is only 1 or 2 places MAX that i ever need the numbers, i tend to always use say $query['name'] rather than $query[0] or whatever heh.

I am printing out the array to test and it shows the correct amount in the array.

The problem is also not with $pagination_query i have not touched that (plus its working perfectly other places :)), it is this page i have re-written so it is in this code the problem actually lies.

The problem i am guessing is my foreach loop which is here, warning its semi-big:
[php]
        // now loop through the posts
        foreach ($this->post_array as $post)
        {    
            // add 1 to the counter for the post
            $this->post_count++;
            
            // get in the moderator options
            $this->moderator_options();
            
            // signature sorting for text and signature picture
            $signature_top = '<div class="content">';
            
            $signature_text = '';
            if (!empty($post['signature']))
            {
                $signature_text = "{$post['signature']}<br />";
            }  
            
            $sigpic = '';    
            if (!empty($post['sigpic']))
            {
                $sigpic = "<img src=\"{$site_config['url']}images/uploads/{$post['sigpic']}\" alt=\"member sigpic\" />";
            }
                    
            $signature_bottom = '</div>';
            
            $signature_finish = '';    
            if (!empty($signature_text) || !empty($sigpic))
            {
                $signature_finish = $signature_top . $signature_text . $sigpic . $signature_bottom;
            }
                    
            // avatar sorting
            if (!empty($post['avatar']))
            {
                $avatar = "<img src=\"{$site_config['url']}/images/uploads/{$post['avatar']}\" alt=\"user avatar\" /><br />";
            }
            
            else
            {
                $avatar = "<img src=\"{$site_config['url']}/images/noavatar.gif\" alt=\"no avatar\" /><br />";
            }
            
            if ($post['author'] == 2)
            {
                $profile_link = $lang['guest'];
                $post_count = '';
            }
            
            else
            {
                if (!empty($post['colour']))
                {
                    $profile_link = "<a href=\"profile.php?info={$post['member_id']}\"><span style=\"color: {$post['colour']};\">{$post['username']}</span></a>";
                }
                            
                else
                {
                    $profile_link = "<a href=\"profile.php?info={$post['member_id']}\">{$post['username']}</a>";
                }
                $post_count = "{$lang['posts']} {$post['post_count']}";
            }
                
            // if it has been edited
            if (!empty($post['last_edited']))
            {
                $edited_time = $pxb->time_zone($post['last_edited'], $_SESSION['timezone']);
    
                $edited = "<em>{$lang['post_edited']} {$edited_time}</em>";
            }
            
            // setup the page
            if (!isset($_GET['pageno']))
            {
                $postpage = '&amp;pageno=1';
            }
                        
            else
            {
                $postpage = "&amp;pageno={$_GET['pageno']}";
            }
            
            if ($parray['reply'] == 1)
            {
                if ($this->locked == 0)
                {
                    $quote_image = "<div style=\"float:right\"><a href=\"newreply.php?tid={$_GET['tid']}&amp;forum_id={$this->forum_id}&amp;quote={$post['post_id']}\"><img src=\"templates/{$site_config['template']}/images/quote.gif\" alt=\"quote image\" /></a>";
                }
                    
                else if ($this->locked == 1)
                {
                    if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2)
                    {
                        $quote_image = "<div style=\"float:right\"><a href=\"newreply.php?tid={$_GET['tid']}&amp;forum_id={$this->forum_id}&amp;quote={$post['post_id']}\"><img src=\"templates/{$site_config['template']}/images/quote.gif\" alt=\"quote image\" /></a>";
                    }
                }
            }
            
            else
            {
                $quote_image = '&nbsp;';
            }            
            
            // the topic itself
            if ($post['is_topic'] == 1)
            {
                $topic_date = $pxb->time_zone($post['topic_date'], $_SESSION['timezone']);
                
                // get the topic options
                $topic_options = '';
                
                if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2 || $post['author'] == $_SESSION['member_id'])
                {
                    $topic_options .= " <a href=\"editpost.php?pid={$post['post_id']}&amp;t\" class=\"topicoptions\">{$lang['edit']}</a>";
                }
            
                if ($parray['reply'] == 1)
                {
                    if ($this->locked == 0)
                    {
                        $topic_options .= " <a href=\"newreply.php?tid={$_GET['tid']}&amp;forum_id={$post['forum_id']}\" class=\"topicoptions\">{$lang['reply']}</a>";
                        
                        $quote_image = "<div style=\"float:right\"><a href=\"newreply.php?tid={$_GET['tid']}&amp;forum_id={$this->forum_id}&amp;quote={$post['post_id']}\"><img src=\"templates/{$site_config['template']}/images/quote.gif\" alt=\"quote image\" /></a>";
                    }
                    
                    else if ($this->locked == 1)
                    {
                        if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2)
                        {
                            $topic_options .= " <a href=\"newreply.php?tid={$_GET['tid']}&amp;forum_id={$post['forum_id']}\" class=\"topicoptions\">{$lang['reply']}</a>";
                        }
                    }
                }
            
                else
                {
                    $topic_options = '&nbsp;';
                    $quote_image = '&nbsp;';
                }
                
                // if there is a poll then get the poll info and show it above the topic table
                if ($post['poll'] == 1)
                {
                    $this->poll($topic_id);
                }
                
                echo eval($templating->load('viewtopic', 'topictable'));
            }
            
            // the reply posts
            else
            {
                $post_date = $pxb->time_zone($post['post_date'], $_SESSION['timezone']);
                
                // reset the reply options for the next one
                $this->reply_options = '';
                        
                if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2)
                {
                    $this->reply_options .= " <a href=\"topicoptions.php?pid={$reply['post_id']}&amp;tid={$reply['topic_id']}&amp;fid={$this->forum_id}&amp;deletereply\" class=\"topicoptions\">{$lang['delete']}</a> ";                   
                }
                        
                if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2 || $_SESSION['member_id'] == $reply['author'])
                {
                    $this->reply_options .= " <a href=\"editpost.php?pid={$reply['post_id']}\" class=\"topicoptions\">{$lang['edit']}</a> ";
                }
                                
                if ($parray['reply'] == 1)
                {
                    $this->reply_options .= " <a href=\"newreply.php?tid={$_GET['tid']}&amp;forum_id={$this->forum_id}\" class=\"topicoptions\">{$lang['reply']}</a>";
                }
        
                else
                {
                    $this->reply_options .= '&nbsp;';
                }               

                
                echo eval($templating->load('viewtopic', 'replytable'));
            }
        }
[/php]

---

### Post by smartbei on 2009-07-03
I would really recommend replacing:
[php]
            if (!empty($post['signature']))
            {
                $signature_text = "{$post['signature']}<br />";
            }
            
            else
            {
                $signature_text = '';
            }
[/php]
with:
[php]
            $signature_text = '';
            if (!empty($post['signature']))
            {
                $signature_text = "{$post['signature']}<br />";
            }
[/php]
To me it seems far more readable, and cuts your code nearly in half. I would also put the opening bracket on the same line as the if, but that is less significant.

since you only have one echo in the whole foreach (two, but they are mutually exclusive), you could print out (maybe to a file) the exact post you are going to be outputting, along with a print_r of the post, and so check if truly you are running through the post twice, with slightly different data, or if there is some odd logic bug.

---

### Post by ELD on 2009-07-03
I don't like the opening brackets on the same line as the if, it is phpbb style of coding, theres a special name for it i can't remember, makes code a lot easier to read.

You are right about the but you posted though, have changed that and other parts and updated the code in the post above.

I have actually found out the problem does lie in the array set the the sql, it seems to add the extra posts into it there so i don't think the problem actually is the foreach loop:
Look at this post for example:
[http://www.prxa.info/area51/viewtopic.php?tid=1](http://www.prxa.info/area51/viewtopic.php?tid=1)

Number 3 in the array shouldn't be there. And so it is echod out in the foreach loop, which is right since it is in the array, but the array is wrong. So is it a problem with the way i grab it with the sql?

```

        SELECT 
            t.topic_id,
            t.forum_id,
                t.author,
            t.title,
            t.date AS topic_date,
            t.replies,
                t.locked,
            t.sticky,
                t.important,
                t.poll,
                t.last_reply_time,
                t.members_read,
            p.post_id,
            p.topic_id, 
            p.author,
            p.text,
            p.date AS post_date,
            f.fid,
                f.name AS forum_name,
            g.colour,
            m.member_id,
                m.username,
                m.signature,
            m.sigpic,
                m.post_count,
                m.avatar,
                m.last_seen_fid
        FROM 
            `{$prefix}posts` p
        INNER JOIN 
            `{$prefix}topics` t ON p.topic_id = t.topic_id
        INNER JOIN
            `{$prefix}members` m ON p.author = m.member_id OR t.author = m.member_id
        INNER JOIN
            `{$prefix}groups` g ON m.group = g.id
        INNER JOIN 
            `{$prefix}forums` f ON t.forum_id = f.fid
        WHERE 
            p.topic_id = {$topic_id}
        ORDER BY 
            p.post_id ASC,
            p.is_topic DESC

```I think the problem may be this bit:
```

        INNER JOIN
            `{$prefix}members` m ON p.author = m.member_id OR t.author = m.member_id

```

---

### Post by ELD on 2009-07-03
Yeah it was that part of my sql, took out the or and its fixed :)

---

### Post by cpetercarter on 2009-07-03
Glad you found the problem.

For the record, the most succinct way of writing:
[PHP] if (!empty($post['signature']))
            {
                $signature_text = "{$post['signature']}<br />";
            }
            
            else
            {
                $signature_text = '';
            }  [/PHP]
is:
[PHP]$signature_text = (!empty($post['signature'])) ? $post['signature']."<br />" : "";[/PHP]

---

### Post by ELD on 2009-07-03
Thanks but i would never code like that, i prefer easy to understand code over shorter code, it is for an application i develope currently available for free, and i would like users to easily read and modify the code.

Anyway it's fixed, thanks for all the replies.

---

### Post by Mirge on 2009-07-03
> **cpetercarter said:**
> Glad you found the problem.

For the record, the most succinct way of writing:
[php] if (!empty($post['signature']))
            {
                $signature_text = "{$post['signature']}<br />";
            }
            
            else
            {
                $signature_text = '';
            }  [/php]is:
[php]$signature_text = (!empty($post['signature'])) ? $post['signature']."<br />" : "";[/php]

> **ELD said:**
> Thanks but i would never code like that, i prefer easy to understand code over shorter code, it is for an application i develope currently available for free, and i would like users to easily read and modify the code.

Anyway it's fixed, thanks for all the replies.

I honestly find
```

$signature_text = (!empty($post['signature'])) ? $post['signature']."<br />" : "";

```

more readable... just my .02 cents though :)

---

### Post by Can+~ on 2009-07-03
You could also omit the {}

[PHP]
if (!empty($post['signature']))
    $signature_text = "{$post['signature']}<br />";
else
    $signature_text = '';
[/PHP]

---

### Post by c0mput3r_n3rD on 2009-07-03
I don't know sql, how ever I find it easier to make a lot of nested if statements into functions.  I find it to keep track of.  :)

---

### Post by Can+~ on 2009-07-04
Taking a peek at the code, besides being huge and having some reiterative parts, what most annoys me is the use of "magic numbers".

[PHP]$_SESSION['group'] == 1 || $_SESSION['group'] == 2[/PHP]

One way you can solve this is issue is creating a "permissions mask".

A cheap, quick way to implement it, is using PHP's "dictionaries":

[PHP]
//                               user0  user1  user2
$mask = array("action1" => array(false, true , true),
              "action2" => array(false, true , true),
              "action3" => array(false, true , false)
)
[/PHP]

(I assumed that user0 is unregistered or something) Now, something like this:

[PHP]if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2)[/PHP]

Could be rewritten as

[PHP]if ($mask["quote_image"][$_SESSION['group']])[/PHP]

Then, in a future day, you may want to remove permission for a certain group, you can make the change on a single place and modify the entire application with almost zero effort. This is specially useful if you're going to build a multi-user multi-permissions level, say, user's that can (guessing this is code is to build a forum) do other tasks, you may even consider allowing the creation of permission dynamically.

As the mask grows, you may consider it moving it to a database table or binary file.

---

### Post by ELD on 2009-07-04
> **Can+~ said:**
> Taking a peek at the code, besides being huge and having some reiterative parts, what most annoys me is the use of "magic numbers".

[php]$_SESSION['group'] == 1 || $_SESSION['group'] == 2[/php]One way you can solve this is issue is creating a "permissions mask".

A cheap, quick way to implement it, is using PHP's "dictionaries":

[php]
//                               user0  user1  user2
$mask = array("action1" => array(false, true , true),
              "action2" => array(false, true , true),
              "action3" => array(false, true , false)
)
[/php](I assumed that user0 is unregistered or something) Now, something like this:

[php]if ($_SESSION['group'] == 1 || $_SESSION['group'] == 2)[/php]Could be rewritten as

[php]if ($mask["quote_image"][$_SESSION['group']])[/php]Then, in a future day, you may want to remove permission for a certain group, you can make the change on a single place and modify the entire application with almost zero effort. This is specially useful if you're going to build a multi-user multi-permissions level, say, user's that can (guessing this is code is to build a forum) do other tasks, you may even consider allowing the creation of permission dynamically.

As the mask grows, you may consider it moving it to a database table or binary file.

Thanks for the input i will take it under advisement, it would be a bit intensive to have an array like that with each user, imagine a users table with 100k+ users...?

> **Mirge said:**
> um ok?

Yeah sorry what? I don't get it either! All i did was express i won't code like that, we all have our own preference?

---

### Post by Can+~ on 2009-07-04
> **ELD said:**
> Thanks for the input i will take it under advisement, it would be a bit intensive to have an array like that with each user, imagine a users table with 100k+ users...?

It's not "per user", that's why it's called a mask. It's a single array in memory that works based on the number you're calling $_SESSION['group'].

For example, this forum has masks, one is called (for example) "registered user mask" which let's you post and view posts, there must be a "global moderator mask" that let's users registered in that group delete and pin topics, etc.

The mask is loaded once into memory for all users.

---

### Post by ELD on 2009-07-04
That is an interesting way to do it actually, i will need to look into it more to properly understand it though, as currently to add permissions for a new group it would need to be hard coded in (as you can tell).

From what i can see something like:
[php]
$mask = array("post" => array(false, true , true),
              "reply" => array(false, true , true),
              "delete" => array(false, true , false)
)  
[/php]

Right or no? Although thinking on it i do something similair in my actual permissions system. Those group session bits are purly for admin and super moderators (which can do everything, so in my eyes it should stay as it is?)

Another dilema i have you can read about here (you seem to know your stuff!):
[http://www.prxa.info/forum/viewtopic.php?tid=161](http://www.prxa.info/forum/viewtopic.php?tid=161)

---

### Post by Can+~ on 2009-07-04
> **ELD said:**
> Right or no? Although thinking on it i do something similair in my actual permissions system. Those group session bits are purly for admin and super moderators (which can do everything, so in my eyes it should stay as it is?)

You're trying to solve the problem for the "now", but not for the "tomorrow". [Scalability]("http://en.wikipedia.org/wiki/Scalability") is not a keyword reserved just for hardware, but for software design too.

> **ELD said:**
> 
Another dilema i have you can read about here (you seem to know your stuff!):
[http://www.prxa.info/forum/viewtopic.php?tid=161](http://www.prxa.info/forum/viewtopic.php?tid=161)

I don't know how your current table layout is to provide the "most recent post" in a category. Seems like a problem of recursion though, try to solve the problem for the common lowest denominator and then expand it for it's parents.

---

### Post by ELD on 2009-07-04
> **Can+~ said:**
> You're trying to solve the problem for the "now", but not for the "tomorrow". [Scalability]("http://en.wikipedia.org/wiki/Scalability") is not a keyword reserved just for hardware, but for software design too.



I don't know how your current table layout is to provide the "most recent post" in a category. Seems like a problem of recursion though, try to solve the problem for the common lowest denominator and then expand it for it's parents.

Forgive me but i don't see what is wrong with it for the future? Admin and Super Mods won't change that is why they are static.

I tried doing some recursive work for 4 hours to get it to work, and started over as i just couldn't get it to work.
What i need is some sql to grab all forums where "parent = 0" and then loop down through them. Only way i know of would be nested sql statements but again they are static, i need it to find all of them.

---

### Post by Can+~ on 2009-07-04
> **ELD said:**
> Forgive me but i don't see what is wrong with it for the future? Admin and Super Mods won't change that is why they are static.

But what if you want to add semi-moderators that can post reply and edit, but can't delete. Or what if you want to add extra functionality?

> **ELD said:**
> I tried doing some recursive work for 4 hours to get it to work, and started over as i just couldn't get it to work.
What i need is some sql to grab all forums where "parent = 0" and then loop down through them. Only way i know of would be nested sql statements but again they are static, i need it to find all of them.

Say that each "category" has a field named "last_post" which points to the last post.

Then, a trigger on the "posts" table ON DELETE/INSERT find the newest post. And also add a trigger ON UPDATE on the "category" table that "if I have been updated and I have a parent != 0, update him too".

This will create a recursive trigger call from bottom-up.

---

### Post by ELD on 2009-07-04
I already do a recursive trigger though, which works great, i have a field called "last_post_id" in my "forums" table which will change the forum the topic is going into, that forums parent, the next and the next and so on (but the problem with that comes later).

Trouble is when you want to delete that topic you then need to loop through all the forums inside the top-most-level and find the latest post for each one, if you see what i mean.
If you simply delete a topic from a forum where a subforum has a newer post, then it will all bugger up.
And the problem arises when you find a forum that has two subforums.

---

### Post by Can+~ on 2009-07-04
> **ELD said:**
> I already do a recursive trigger though, which works great, i have a field called "last_post_id" which will change the forum the topic is going into, that forums parent, the next and the next and so on.

Only trouble is when you want to delete that topic you then need to loop through all the forums inside the top-most-level and find the latest post for each one, if you see what i mean.

Exactly, you're implementing a top->bottom algorithm, from root to leaves. The event is actually occurring on one of the "leaves", and it should tell his parent what changed and then trigger it recursively.

Split it in this two problems:

"Find the newest post on my section"
"Tell my parent (if I have one) that a change has been made"

Those are the two only steps of this recursion.

[IMG]http://img.photobucket.com/albums/v517/CanXp/tellmyparent.gif[/IMG]

---

### Post by ELD on 2009-07-04
That is essentially what i am trying to acheive. Which i think that part of things i have working fine.

The problem arises when say you go from child213 up to child21, if child21 has a partner forum (so child2 actually has child 21 and 22) i then need to do a seperative recursive function to look for seperate parent forums, their children etc. Also if "child213" has it's own children they need to be checked to see if they have a post that is newer than "child213".

Which is why i need to start from "child 213", check its subforums and then move up.

---

### Post by Can+~ on 2009-07-04
> **ELD said:**
> The problem arises when say you go from child213 up to child21, if child21 has a partner forum (so child2 actually has child 21 and 22) i then need to do a seperative recursive function to look for seperate parent forums, their children etc.

And why not just ask their "last_post" field instead of jumping inside?

1. The first time a post is changed it looks for the newest and tells the corresponding category. (TRIGGER on post table)
2. The category now looks for the newest between it's categories, but NOT looking into it's posts, it just requests the last_post. (recursive TRIGGER on category table)
3. Repeat 2 until parent == 0.

I think I finally nailed down your problem, doing a search for the last post must be made ONCE. Then you step into a recursion that looks for only for the last_post.

---

### Post by ELD on 2009-07-04
To better help you understand i think i have nailed it here is my code:

[php]
    // this starts it all off, it check the current forum, then move onto its subforums, subsub forum etc, then it loops back here for the next level
    function this_forum_recursive($forumid)
    {
        global $prefix, $db;
        // now we need to find the next topic available 
        $sql_find_last_topic = "
        SELECT 
            t.`topic_id`, 
            t.`last_reply_time`, 
            f.`parent` 
        FROM 
            `{$prefix}topics` t 
        INNER JOIN 
            `{$prefix}forums` f ON f.fid = t.forum_id WHERE t.`forum_id` = {$forumid} 
        ORDER BY 
            t.`last_reply_time` DESC LIMIT 1"; 
        $query_last_topic = $db->query($sql_find_last_topic);

        // if there is no last post
        if ($db->num_rows($query_last_topic) == 0)
        {
            // we need to find the parent forum
            $sql_parent = "SELECT `parent` FROM `{$prefix}forums` WHERE `fid` = {$forumid}";
            $query_parent = $db->query($sql_parent);
            $the_parent = $db->fetch_array($query_parent);

            $this->parent = $the_parent['parent'];
            $this->find_last_topic_subforum_recursive($forumid, 0, 0, $forumid);
        }

        // if we have found that this forum has another post in it
        else
        { 
            $last_topic = $db->fetch_array($query_last_topic);
            $this->parent = $last_topic['parent'];
            $this->find_last_topic_subforum_recursive($forumid, $last_topic['last_reply_time'], $last_topic['topic_id'], $forumid);
        }
    }

    // this will make sure we update the forums last topic correctly
    function find_last_topic_subforum_recursive($forumid, $last_reply_time, $topic_id, $this_forum_id)
    {
        global $prefix, $db;

        // we need to find if the forum we need to update has any subforums, if so find the one with the newest post time (last_reply_time)
        $sql_forum = "
        SELECT 
            f.`fid`,
            t.`last_reply_time`,
            t.topic_id 
        FROM 
            `{$prefix}forums` f
        INNER JOIN
            `{$prefix}topics` t ON f.`last_topic_id` = t.`topic_id`
        WHERE 
            f.`parent` = {$forumid} AND t.`last_reply_time` > {$last_reply_time}
        ORDER BY
            t.`last_reply_time` DESC LIMIT 1";

        $query_forum = $db->query($sql_forum);
        
        // have we found one?
        if ($db->num_rows($query_forum) == 1)
        {
            $forum = $db->fetch_array($query_forum);

            $this->last_post_id = $forum['topic_id'];
            $this->last_post_time = $forum['last_reply_time'];

            // now we need to see if this subforum has any subforums of it's own, and filter by which one has the newest post time (last_reply_time)
            $sql_forum = "
            SELECT 
                f.`fid`,
                t.`last_reply_time`,
                t.topic_id
            FROM 
                `{$prefix}forums` f
            INNER JOIN
                `{$prefix}topics` t ON f.`last_topic_id` = t.`topic_id`
            WHERE 
                f.`parent` = {$forum['fid']} AND t.`last_reply_time` > {$forum['last_reply_time']}
            ORDER BY
                t.`last_reply_time` DESC LIMIT 1";

            $query_forum = $db->query($sql_forum);

            // if we did find one
            if ($db->num_rows($query_forum) == 1)
            {
                $forum = $db->fetch_array($query_forum);

                // set the latest post id to the latest found one
                $this->last_post_id = $forum['topic_id'];
                $this->last_post_time = $forum['last_reply_time'];

                // now loop the latest found subforum to see if it has any (this will go on until we get to the last child)
                $this->find_last_topic_recursive($forum['fid'], $forum['last_reply_time'], $this->last_post_id);
            }
        }
        
        // if we havn't then they are old posts, there are no posts or there are actually no child forums, then set the global strings to the originals
        else
        {
            // set them to the originals, so we can now use these when going up to the next level
            $this->last_post_id = $topic_id;
            $this->last_post_time = $last_reply_time;

            $this->this_forum_recursive($this->parent);
        }    
    }
[/php]Feel free to criticize (and try not to be to hard on me ;)). I am going to test it now.

Ugh that didn't work at all, i'm just about ready to give up :(

---

