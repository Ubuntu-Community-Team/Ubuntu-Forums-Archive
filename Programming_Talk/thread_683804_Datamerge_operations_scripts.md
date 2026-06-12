---
title: "Datamerge operations scripts"
date: 2008-01-31
forum: Programming Talk
---

### Post by saphil on 2008-01-31
I have several data files, that are currently not similar in structure.  Different number of fields per row, and the similar fields are named different things.

I am building a catalog in Drupal, and realized that Drupal doesn't give me a way to add a user-defined text block attached to each instance of product added to the shopping cart.  This may well mean I have to go at figuring out the structure of Drupal to find a way to get the field in there, and thus add to the sum-total of FOSS knowledge in the drupal arena.  This looked like something I would love to look into when I am not on a deadline to get a 3000 sku catalog on the site., so in a blinding flash of insight, I remembered MSOffice merge, that takes an arbbitrary data source and allows you to merge to a custom document.  That would be simple, since I could just normalize the column headings on my data files and go to town with the following source-document and fill in the fields as I want.  Viola! a list of entries that I can use immediately (except for linking the graphic files in.
>    	 	 	 	 	 	    <tr>
            <td>&nbsp;[SKU#-field]
            <p>&nbsp;&quot;9/16&quot; X&nbsp; &quot;2&quot;</p>
            </td>
            <td>
            <p><form target="paypal" action="https://www.paypal.com/cgi-bin/webscr" method="post">
<table><tr><td><input type="hidden" name="on0" value="Imprint Detail">Imprint Detail</td><td><input type="text" name="os0" maxlength="60"></td></tr><tr><td><input type="hidden" name="on1" value="Special Instructions">Special Instructions</td><td><input type="text" name="os1" maxlength="60"></td></tr></table><input type="image" src="https://www.paypal.com/en_US/i/btn/sc-but-03.gif" border="0" name="submit" alt="Make payments with PayPal - it's fast, free and secure!">
<img alt="" border="0" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1">
<input type="hidden" name="add" value="1">
<input type="hidden" name="cmd" value="_cart">
<input type="hidden" name="business" value="email@wherever.com">
<input type="hidden" name="item_name" value="[ItemName-field]">
<input type="hidden" name="item_number" value="[SKU#-field]">
<input type="hidden" name="amount" value="[123.45-field]">
<input type="hidden" name="no_shipping" value="2">
<input type="hidden" name="no_note" value="1">
<input type="hidden" name="currency_code" value="USD">
<input type="hidden" name="lc" value="US">
<input type="hidden" name="bn" value="PP-ShopCartBF">
</form>;</p>
            
            </td>
            <td><img width="200" height="210" alt="" src="[SKU#.jpg-field]" />&nbsp
<p>&nbsp;Image is not shown full size</p>;</td>
        </tr> 

1st problem: MS Office not available.  
2nd problem OpenOffice does not have this functionality (unless I want to hand-enter all data in their data-source format)
This is probably a super easy problem that I missed in school.  I am looking around for examples of perl or python scripts I can modify.  Do you have any suggestions?

---

### Post by lnostdal on 2008-02-01
too .. many .. words

what do you have now (data) .. and what would you like it to be or look like? .. something concrete please

---

### Post by saphil on 2008-02-01
Ok, 
I have a collection of data sources in .csv
I want to run a script that will build web pages by inserting each row of data into a specially prepared template, over and over until the table on the web page has as many rows as the data source.  Like this one (that I did by hand) and pasted into the php page

[http://nynotary.com/i-stamp](http://nynotary.com/i-stamp)

---

