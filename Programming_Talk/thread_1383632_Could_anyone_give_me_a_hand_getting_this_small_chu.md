---
title: "Could anyone give me a hand getting this small chunk of HTML/PHP/CSS working?"
date: 2010-01-17
forum: Programming Talk
---

### Post by hoppipolla on 2010-01-17
Hiya peeps :)  If anyone can help me get this working I will be soooo happy, it's just... it's mainly IE that it breaks in, but I've been having little niggles on Firefox too (I use Chrome myself and it works flawlessly on there as Chrome is awesommme! ^_^ ). Basically though, all I want to do is make the whole thing clickable, assign both ids (or an equivalent effect) to the whole table, as the ids  trigger something else, and center all the tables contents. I would also like it all to work in.. *gulp* ... IE7 ._.

Does anyone have any idea about this? It's proving so tricky, and any help would be very, very much appreciated :)

> <a href="link.php?id=<?php echo $topLink[1]['linkID']; ?>&page=<?php echo $topLink[1]['linkTitle']; ?>" target="_blank"><table style="width: 148px; height: 110px; margin-left: auto; margin-right: auto; text-align: center; vertical-align: middle;" border="0" cellpadding="0" cellspacing="0" id="ddbg">
              <tbody>
                <tr align="center">
                  <td style="vertical-align: middle; text-align: center; height: 22px;"><small><span style="font-family: Helvetica,Arial,sans-serif;"><?php echo $topLink[1]['typeDescription']; ?></span></small><br>
                  </td>
                </tr>
                <tr align="center">
                  <td style="vertical-align: middle; text-align: center; width: 124px; height: 80px; background-repeat: no-repeat;" background="backing.png" id="ddimg">
                  <img style="border: 0px solid;" alt="<?php echo $topLink[1]['linkTitle']; ?>_logo" src="img/<?php echo $topLink[1]['imageLocation']; ?>">
                   </td>
                </tr>
                <tr align="center">
                  <td style="vertical-align: middle; height: 22px; text-align: center;"> <small><small><span style="font-family: Helvetica,Arial,sans-serif;"><?php echo $topLink[1]['linkRating']; ?> dviews 
</span></small></small>
<?php
for($i=0;$i<intval($topLink[1]['linkStars']);$i++)
{
	echo '<img style="width: 16px; height: 16px;" alt="s" src="star.png" />';
}
?>
<br>
                  </td>
                </tr>
              </tbody>
            </table></a>

(I put it in quote tags just so it word wrapped it - is there any other way to do this?)


Thanks,

Hoppi :)

---

### Post by Hellkeepa on 2010-01-17
HELLo!

The PHP tags would be perfect for this.

That said: Rewrite the entire thing, and use semantic HTML to structure your content, and CSS to style it. Tables should not be abused to layout purposes, as they are meant to be used with tabular data. (Time tables, periodic tables, calendres, matrices, and so forth.)

Happy codin'!

---

