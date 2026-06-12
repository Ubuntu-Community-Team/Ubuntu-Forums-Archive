---
title: "I am Stuck"
date: 2012-05-06
forum: Programming Talk
---

### Post by barira on 2012-05-06
Hello everyone!
I am new to this forum. I created a function that was counting user visits at every post.
My function is like this...

[php] 
        function getPostViews($postID)
        {
        $count_key = 'post_views_count';
        $count = get_post_meta($postID, $count_key, true);
        if($count=='')
        
        {
            delete_post_meta($postID, $count_key);
            add_post_meta($postID, $count_key, '0');
            
        }
        return $count;
        }
        function setPostViews($postID)
        {
        $count_key = 'post_views_count';
        $count = get_post_meta($postID, $count_key, true);
        if($count=='')
        
        {
            delete_post_meta($postID, $count_key);
            add_post_meta($postID, $count_key, '0');
            
        }
        else
        {
            $count++;
            update_post_meta($postID, $count_key, $count);
        }
    
        }
[/php]
i called setPostviews on home.php where i was calling posts from loop and the render that.

it was working fine. Now i tried to make it object oriented and its not working the right way...
my object oriented function is
[php]
<?php
class myClass {
    function myClass()
    {
        
    }
    function getPostViews($postID){
          {
        $count_key = 'post_views_count';
        $count = get_post_meta($postID, $count_key, true);
        if($count=='')
        
        {
            delete_post_meta($postID, $count_key);
            add_post_meta($postID, $count_key, '0');  

        }
        return $count;
        }
    }
    function setPostViews($postID)
    {
            {
        $count_key = 'post_views_count';
        $count = get_post_meta($postID, $count_key, true);
        if($count=='')
        
        {
            delete_post_meta($postID, $count_key);
            add_post_meta($postID, $count_key, '0');
            

        }
        else
        {
            $count++;
            update_post_meta($postID, $count_key, $count);

        }
    
        }
    }
}
$mine=new myClass();
$mins= new myClass();
$mine->getPostViews($postID)
?>
[/php]
Can anyone help me in this?
Thanks and looking forward for some cool and helpful replies

---

### Post by lisati on 2012-05-06
*Thread moved to **Programming Talk**.*

---

