---
title: "PHP and CSS problem"
date: 2009-04-23
forum: Programming Talk
---

### Post by Adina on 2009-04-23
I have put this code on a web page :



<p id="thisDay">


<?php
        $thisMonth = date(r);
        echo $thisMonth;
?>


</p>



The output on the page is this:

Thu, 23 Apr 2009 13:00:07 +0200

Now the problem is that I want to change the color of the text output.




Here is the css code: 


 #thisDay {
                color:darkviolet;

        }


The fonts don't change color.. can anyone please tell me what I'm doing wrong?

---

### Post by Peter76 on 2009-04-23
You must have made a typo I guess... When I tried it worked fine. Here is the code I used:

```

<html>
<head>
<style type="text/css">
	#thisDay { color: darkviolet; }
</style>

</head>

<body>
<p id="thisDay">
	<?php
		$thisMonth=date(r);
		echo $thisMonth;
	?>
</p>
</body>
</html>

```

Hope this helps. Good luck

---

### Post by Adina on 2009-04-23
Thank you for your reply. I canged it to class instead of id and now it works.. so I think maybe there's some problems with my css file. I don't know. But thank's again for your help, I really appreciate it!

---

### Post by Reiger on 2009-04-23
Or maybe the PHP code outputs more than 1 element with ID "thisDay"?

---

### Post by odyniec on 2009-04-23
> **Reiger said:**
> Or maybe the PHP code outputs more than 1 element with ID "thisDay"?

That's not likely to be the cause. While it's wrong to have more than one element with the same ID, I think pretty much every browser would still apply the style to all the elements.

---

### Post by tturrisi on 2009-04-25
> **Reiger said:**
> Or maybe the PHP code outputs more than 1 element with ID "thisDay"?

PHP doesn't output elements unless the html tags exist within the php echo.  PHP just spits out the variable as echoed text w/ no markup or style applied.

---

### Post by Reiger on 2009-04-25
Well yes: but webbrowsers are, as per W3C specs, required to *ignore* ID's which already exist elsewhere in the document. Which means that if multiple tags with the id="thisDay" were output only at most 1 tag should see #thisDay CSS applied.

---

