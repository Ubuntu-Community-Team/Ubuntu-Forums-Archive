---
title: "[SOLVED] PHP and Check Boxes"
date: 2008-08-10
forum: Programming Talk
---

### Post by thenetduck on 2008-08-10
Hi

I am creating an app in which I can add cards to piles. When you create a "card" you can add it to multiple piles (a list of cards). I would like to use a checkbox to handle this, however I need to be able to get data about multiple piles checked. 

if that makes sense... 

My question is, how can I create multiple checkboxes with data that changes and then receive that data when submitting the the form? As of now, this is what my displayPiles() function looks like. 

```

 function displayPiles()
            {
                             // Create a new user object. 
              $user = new user();
              $piles = $user->getPiles();
              $pile_list .=  '<tr>';
              $i = 1; // ignore this, it's just an index to keep track of number of piles in a row.
              $row_display = 5; // this is the number of piles per row.
              for ($j=0; $j<sizeof($piles); $j++)
                {
                   
                   if($i%$row_display == 0){$pile_list .='<tr>';}
                         $pile_id = $piles[$j][0];
                         $pile_name = $piles[$j][1];
                         $pile_list .= 
                        '<td valign=top align=center>
                         <input type="checkbox" name="piles" value= ' . ' " ' . $pile_id. ' " ' . ' /><br />' .
                         $pile_name . '<br /> ' . $user->getNumberOfCards($pile_id) .  ' cards in pile' .
                          '</td>' ;
                   if($i%$row_display == 0){$pile_list .='</tr>';}
                }
              $pile_list .= '</tr>';
                return $pile_list;
            }
            
            // Call the function to display the piles. 
            echo displayPiles();


```

What is the proper way to receive/process the $_POST['piles'] name that is generated?

Thanks
The Net Duck

---

### Post by mssever on 2008-08-10
> **thenetduck said:**
> My question is, how can I create multiple checkboxes with data that changes and then receive that data when submitting the the form?
If I understand you correctly, you can give your checkboxes the name somename[] (notice the square brackets). PHP will magically turn such named items into an array $_POST['somename'] (or $_GET). Of course, that means that all items you want in the array have to share the same name (but it's a violation of the standards to give more than one element the same id).

---

### Post by thenetduck on 2008-08-10
Yes that is what I mean. Ok tha worked like acharm. Using var_dump() to see things now. It is very very useful!

Thanks 

The net duck

---

