---
title: "Php echo help please"
date: 2010-04-07
forum: Programming Talk
---

### Post by gdubbs on 2010-04-07
[COLOR=#000000][FONT=verdana]Hello Everyone,


I need a little help with a php page were i want a page to show this text until a job is done.Im working on a game and this is for the job page.

when you look at the page it will say this 

Complete jobs to gain experience, earn money, and level up.

Remember, the bigger your family, the more experience and money you'll receive. Unlock harder jobs by leveling up.
(Reach level 9 to unlock more jobs)

And in same area after you do the job i want the job done to appear in same area


here is the code im working with[PHP] <TD width="760" style="PADDING-RIGHT: 30px"><H1>
            
            <span class="paragraph2" style="PADDING-TOP: 5px"><?php
    if($error!="")
    {
    ?> </span><?php echo $err = ErrorMessage($error);?>

    <?php
    }
    ?>
            Complete jobs to <STRONG>gain experience, earn money, and level 
            up.</STRONG></H1>
              <P style="FONT-SIZE: 13px">Remember, the bigger your family, the more 
                experience and money you'll receive. Unlock harder jobs by leveling 
                up.</P> 
            <?php
        $level = $user["level"];
        $nextLevelRow = mysql_fetch_array(db_execute_return("Select level from jobs where level>".$level." Order by level DESC Limit 1;"));
    $nextLevel = $nextLevelRow["level"];
    
        ?>
              <P style="PADDING-TOP: 5px" class=paragraph2>(Reach <?php echo "level " . $nextLevel = $level+1;?> to unlock more 
                jobs)              </P>
       
</TABLE> [/PHP] [COLOR=#000000][FONT=verdana]now im sure i can echo it but im not sure on how to do it any help would be great[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by tgalati4 on 2010-04-07
There are lots of ways to print out results using php including print, printf, and echo.  Some echo-related syntax can be found:

[http://www.php.net/manual/en/language.basic-syntax.php](http://www.php.net/manual/en/language.basic-syntax.php)

There are different ways of blocking/escaping php code with echo.  See some of the posted examples to figure out which method is best for you.

To keep the results on screen would require some sort of while loop during the condition of current level.

[http://www.php.net/manual/en/control-structures.while.php](http://www.php.net/manual/en/control-structures.while.php)

---

### Post by Ravenshade on 2010-04-07
[www.w3schools.com](www.w3schools.com) helped me out quite a lot when learning php. From what I remember the syntax was echo 'line here'; 

can't be certain of that though.

---

