---
title: "keep track of score in taboo in php"
date: 2008-10-23
forum: Programming Talk
---

### Post by blackphiber on 2008-10-23
a little bit unsure of myself when it comes to php since everything is done on the server side.

I am working on writing a game based on the word game Taboo from Milton Bradley. Hopefully someone here can help me out, I cannot see this being too difficult of a situation to figure out, however, I am having trouble, thus I am asking for help.

I need help with keeping track of the score.

a good example of what I am shooting for is [www.playtaboo.com](www.playtaboo.com)

I would like to display a random taboo card, and below the card allow the user to click on either correct or incorrect and when they click on the button, the current teams score will either be incremented, or decremented, and then it should move on to the next team with another random card.

here is what I have (please don't make too much fun of me, it is very far from polished, just a cheap hack atm) so far. I am having trouble keeping track of the score. when the user clicks on either correct or incorrect the form will be submitted (multiple forms on this page...) but I think this will set everything else back to square one... playtaboo.com seems to use:

```
<input value="CORRECT" name="Input" type="button" onclick="location.href='display4.php?act=increase'" />
<input value="PASSED" name="Input" type="button" onclick="location.href='display4.php?act=decrease';" />
<input value="END ROUND" name="Input" type="button" onclick="location.href='display4.php?act=clear'" />
```

and I am not sure how I could implement something similar. would I have to use Sessions or... simplest way to do this?

[PHP]<html>
    <head>
     <title>Taboo</title>
    </head>
    <body>

   <?php
   /*
    *      driver.php
    *      
    *      Copyright 2008 Thomas Wolfe <tomwolfe@gmail.com>
    *      
    *      This program is free software; you can redistribute it and/or modify
    *      it under the terms of the GNU General Public License as published by
    *      the Free Software Foundation; either version 2 of the License, or
    *      (at your option) any later version.
    *      
    *      This program is distributed in the hope that it will be useful,
    *      but WITHOUT ANY WARRANTY; without even the implied warranty of
    *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    *      GNU General Public License for more details.
    *      
    *      You should have received a copy of the GNU General Public License
    *      along with this program; if not, write to the Free Software
    *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
    *      MA 02110-1301, USA.
    */

   <a href="addcard.php">Add Card</a>

   $cardStorage=new cardStorage();
   $card=new card();
   $currentTeam=1;
   //$timestart=time();
   //$timeend=time();
   // 

   //$time=htmlentities($_GET["time"]);
   $maxNumTabooWords=htmlentities($_GET["maxNumTabooWords"]);
   $numCards=htmlentities($_GET["numCards"]);
   $numTeams=htmlentities($_GET["numTeams"]);
   $copyMaxNumTabooWords=$maxNumTabooWords;
   
   $correct=htmlentities($_GET["correct"]);
   $incorrect=htmlentities($_GET["incorrect"]);

   if ($maxNumTabooWords == '' | $numCards == '' | $numTeams == '')
   {
      echo('
      <form action="driver.php" method="get">
      Maximum Number of taboo words: <input type="text" name="maxNumTabooWords" />
      Number cards to play for game: <input type="text" name="numCards" />
      Number of teams: <input type="text" name="numTeams" />
      <input type="submit" value="submit options" />
      </form>');
   }
   else if ($time<2 | $maxNumTabooWords<1 | $numCards<3 | $numTeams<2 !is_numeric($time) | !is_numeric($maxNumTabooWords)
    | !is_numeric($numCards) | !is_numeric($numTeams) | $numCards<$numTeams)
   {
   echo('
      Valid input:
      must be numeric
      Number of cards must be greater than # of teams
      time must be over 2 seconds
      Maximum number of taboo words must be over 1
      number of cards to pay must be over 3
      number of Teams must be over 2
      <form action="driver.php" method="get">
      Time (in seconds) between turns: <input type="text" name="time" />
      Maximum Number of taboo words: <input type="text" name="maxNumTabooWords" />
      Number cards to play for game: <input type="text" name="numCards" />
      Number of teams: <input type="text" name="numTeams" />  
      <input type="submit" value="submit options" />
      </form>');
   }
   else
   {
      for(i=0;i<$numTeams;i++)
      {
         arrayTeam[i]=new Team();
         i++;
      }
         
      while($numCards!=0)
      {
         if($currentTeam==$numTeams)
         {
            $currentTeam=1;
         }
         $card=cardStorage->getRandomCard();
         $card->getTitle();
         $tabooWords=$card->getTabooWords(); // should store array of all taboo words for card
         $numTabooWords=sizeof($tabooWords); // stores num of elements in array
         
         while($numTabooWords!=0 && $copyMaxNumTabooWords!=0)
         {
            echo "<p>$tabooWords";
            $numTabooWords--;
            $copyMaxNumTabooWords--;
         }
         echo('
         <form action="driver.php" method="get">
         <input type="hidden" name="correct" value="correct" />
         <input type="submit" value="correct" />
         </form>
         <form action="driver.php" method="get">
         <input type="hidden" name="incorrect" value="incorrect" />
         <input type="submit" value="incorrect" />
         </form>');
         
         $if($correct==correct)
         {
            $arrayTeam[$currentTeam]->incScore();
         }
         else if($incorrect==incorrect)
         {
            $arrayTeam[$currentTeam]->incScore();
         }
         else
         {
            echo "weird error, was neither correct or incorrect";
         }
         
         $numCards--;
         $currentTeam++;
      }
            
   }
   ?>
    </body>
   </html>[/PHP]

---

