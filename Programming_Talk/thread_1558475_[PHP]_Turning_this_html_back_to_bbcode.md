---
title: "[PHP] Turning this html back to bbcode"
date: 2010-08-22
forum: Programming Talk
---

### Post by ELD on 2010-08-22
Hi all, apologies to start with i'm crap at explaining.

Basically i have an item bbcode which replaces a number with a thumbnail and info on that item:
[php]
    function parse_items($text)
    {
        global $db;
        
        $pattern = '#\[item\]([0-9]+)\[/item\]#mi';

        preg_match_all($pattern, $text, $matches);
        
        foreach ($matches[1] as $match)
        {
            $sql_item_match = "SELECT * FROM `items` WHERE `id` = {$match}";
            
            $query_item_match = $db->query($sql_item_match);
            
            $item_match = $db->fetch_assoc($query_item_match);
            
            // lets see if we have a screenshot so we can use it's thumbnail shall we?
            $sql_shot = "SELECT `image_filename` FROM `item_screenshots` WHERE `accepted` = 1 AND `item_id` = {$item_match['id']} LIMIT 1";
            $query_shot = $db->query($sql_shot);
        
            if ($db->num_rows($query_shot) == 1)
            {
                $shot = $db->fetch_assoc($query_shot);
        
                $thumbnail = "<a href=\"uploads/images/{$shot['image_filename']}\" rel=\"lytebox\"><img src=\"uploads/images/thumbnails/{$shot['image_filename']}\" alt=\"\" /></a>";
            }
        
            else
            {
                $thumbnail = "<img src=\"images/noshot.jpg\" alt=\"\" />";
            }
            
            $replace = "<div class=\"item1\">
                <a href=\"item.php?iid={$item_match['id']}\">{$item_match['name']}</a><br />
                <span style=\"float: left; padding-right: 6px;\">{$thumbnail}</span>{$item_match['short_description']}<br />
                Version: {$item_match['version']}
                <br style=\"clear: both;\" />
            </div>";
            
            $text = preg_replace($pattern, $replace, $text);
        }    
        
        return $text;
    }
[/php]

I am trying to now make an un-parser to turn the html that "[item]12[/item]" makes back into that bbcode, but i can't seem to get it to work:
[php]
    function undo_items($text)
    {
        // change quote html back to bbcode
        $pattern = "#<div class=\"item1\">
                <a href=\"item.php?iid=([0-9]+)\">(.*?)</a><br />
                <span style=\"float: left; padding-right: 6px;\">(.*?)</span>(.*?)<br />
                Version: (.*?)
                <br style=\"clear: both;\" />
            </div>#mix";
        
        $replace = '[item]$1[/item]';
        
        while(preg_match($pattern, $text))
        {
            $text = preg_replace($pattern, $replace, $text);
        }

        return $text;
    }
[/php]

I know theres probably something i'm overlooking as usual.

---

### Post by Hellkeepa on 2010-08-22
HELLo!

Well, beside the fact that the HTML code looks far too complex for what I *think* it does; That you should have put all of the CSS inside the CSS file, and just used classes instead; The problem is that you haven't escaped some of the literals in the string.
More specifically the question mark in the URL gets interpreted as a control character, making the "p" before it optional.

You could also replace the "[0-9]" with a simple "\d", and the ".*?" should be replaced with "[^<]+". Latter should be a bit faster.

Happy codin'!

---

### Post by ELD on 2010-08-23
What other characters do i need to escape?

Apart from one bit of css it's as compact as it can be.

---

