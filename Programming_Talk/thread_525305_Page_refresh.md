---
title: "Page refresh"
date: 2007-08-14
forum: Programming Talk
---

### Post by rock freak on 2007-08-14
Right hopefully ill be bale to sum this up ina  line or to!!

What i need to do is have a page load up then auto refresh once straight away as it doesnt always update my mysql query..

Hopefully that makes sense.

Cheers
Ollie

---

### Post by ankursethi on 2007-08-14
What, a web page? Use a JavaScript function for refreshing the page. I think it was document.reload() or something. Check it out on the web.

---

### Post by LaRoza on 2007-08-14
> **ankursethi said:**
> What, a web page? Use a JavaScript function for refreshing the page. I think it was document.reload() or something. Check it out on the web.

You can also use document.location and point to the originating page, or use a <meta> refresh.

---

### Post by rock freak on 2007-08-14
I tried the meta refresh but it jsut sat there refreshign every Xsecs then :( just need it to do it once!! 

Ill give javascript ago! Not used any for ages now!!

---

### Post by christopherZA on 2007-08-15
Hi

If your running PHP5 you can use the following:

  
[INDENT] [B] function pageRefreshed() {
    return $_SERVER['HTTP_CACHE_CONTROL'] == 'max-age=0' ? true : false;
    }
 
  
  if ( !pageRefreshed () ) {
     
       // -- insert your sql into database
    
    } 

   ...
   ...
   // -- Display your data ...
  ...[/B]
[/INDENT]

The functions calls an apache param to check if this page has been refreshed. I use this in my applications where resubmitting a form can cause problems.

To do a redirect I use the following:


[INDENT]?>
 [B]       <SCRIPT TYPE="text/javascript">
        <?php echo "parent.location='SummaryPage.php?item_id=$item_id'";      ?>
        //-->
        </SCRIPT>
<?php[/B]
[/INDENT]

The above redirects to a page that displays the details for one form ( $item_id is record id). You could also do something like this instead if you don't need to pass any params:


[INDENT]?>
  [B]      <SCRIPT TYPE="text/javascript">
        parent.location='Page.php' 
        //-->
        </SCRIPT>[/B]
<?php
[/INDENT]

Hope this helps

---

