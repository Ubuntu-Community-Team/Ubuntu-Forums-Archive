---
title: "[php]  Preg match loop returns the same"
date: 2010-10-23
forum: Programming Talk
---

### Post by ELD on 2010-10-23
Basically i am preg matching through a certain bbcode to grab the corresponding database row that it finds the id of between item bbcode tags:

[php]
        $pattern = '#\[item\]([0-9]+)\[/item\]#i';

        preg_match_all($pattern, $text, $matches);
        
        foreach ($matches[1] as $match)
        {
            $sql_item_match = "SELECT * FROM `items` WHERE `id` = {$match}";
            
            $query_item_match = $sdb->query($sql_item_match);
            
            $item_match = $sdb->fetch_assoc($query_item_match);
            
            // lets see if we have a screenshot so we can use it's thumbnail shall we?
            $sql_shot = "SELECT `image_id`, `image_filename` FROM `item_screenshots` WHERE `accepted` = 1 AND `item_id` = {$item_match['id']} LIMIT 1";
            $query_shot = $sdb->query($sql_shot);
        
            if ($sdb->num_rows($query_shot) == 1)
            {
                $shot = $sdb->fetch_assoc($query_shot);
                
                $thumbnail = "uploads/images/thumbnails/{$shot['image_filename']}";
        
                if (!file_exists($thumbnail))
                {
                    $core->make_thumbnail($shot['image_filename']);
                }
        
                $thumbnail = "<a href=\"screenshot.php?sid={$shot['image_id']}\" rel=\"lytebox\" title=\"&lt;a href=&quot;screenshot.php?sid={$shot['image_id']}&quot;&gt;Click here to view the screenshot on it's own.&lt;/a&gt;\"><img src=\"uploads/images/thumbnails/{$shot['image_filename']}\" alt=\"\" /></a>";
            }
        
            else
            {
                $thumbnail = "<img src=\"images/noshot.jpg\" alt=\"\" />";
            }
            
            $replace = "<div class=\"item\"><strong>GOL Database Entry</strong><br /><a href=\"item.php?iid={$item_match['id']}\">{$item_match['name']}</a><br /><span class=\"thumbnail_left\">{$thumbnail}</span>{$item_match['short_description']}<br />Version: {$item_match['version']}</div>";
            
            $text = preg_replace($pattern, $replace, $text);
        }    
        
        return $text;
[/php]Problem is i have one that finds two item bbcodes in one block of text, i echo'd out "$match" inside the foreach and it shows the seperate ids it found between the item tags, but the replace seems to replace both with the first ones information.

I put an "echo $replace;" right before the preg_replace and it shows both correctly, yet when it runs both items are the same, do i have to do some sort of loop on the replace itself as well?

Does that make sense at all?

So for this text:
[item]1[/item]
[item]2[/item]

It should replace with the html stuff up there to (example)
<some html>1
<some html>2

But it actually does this:
<some html>1
<some html>1

What am i doing wrong for it to replace both with the first one found?

---

