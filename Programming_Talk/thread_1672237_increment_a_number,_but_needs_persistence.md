---
title: "increment a number, but needs persistence"
date: 2011-01-20
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-20
how can this be done?
so that the number will increment +1 every time a button is pushed?
I push the button, but cant get the number to go up
> <?php
$inc=0;

if (!empty($_POST['button'])){
      switch ($_POST['button']){
        case 'button1':
          $yes = 'yes 1';
          echo  'time '.time().'<BR>';
 
          echo 'increment number '.$inc.'<BR>';
          $f = sum();
          echo $f.'<BR>';
          echo 'increment number '.$f.'<BR>';

           $inc = sum();
          echo 'increment number '.$inc.'<BR>';
          echo "pushed button 1".'<BR>';
         
          //echo $inc; 
          //echo $inc;
          $q= "select titles, author from bookdata where id = '$f'";    
          echo "$q".'<BR>';
         
        break;
        case 'button2':
            echo "pushed button 2".'<BR>';
        break;
        case 'button3':
            echo "pushed button 3".'<BR>';
        break;
       

        default:
            echo "????/".'<BR>';            
        break;
      }
     }
 else
 { 
 //$inc = 0;
 }

?>


<form action="increment.php" method="post">
    <div>
    <input type="submit" name="submit" value="submit"/>
    <button type="submit" name="button" value="button1">Button 1</button>
    <button type="submit" name="button" value="button2">Button 2</button>
    <button type="submit" name="button" value="button3">Button 3</button>
    </div>
    </form>

<?php

function sum()
{
   global $inc;
   $inc = $inc + 1;
} 

function sub()
{
   global $inc;
   $inc = $inc - 1;
} 


---

### Post by shadylookin on 2011-01-20
Once a php script has finished executing all the variables are gone. 
A work around is to use hidden inputs to keep values. like

<input type='hidden' name="numOfTimesClicked" value="2"/>

then look for that in the php file

---

