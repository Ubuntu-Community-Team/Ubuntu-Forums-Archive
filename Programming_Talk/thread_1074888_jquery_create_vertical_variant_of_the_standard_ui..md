---
title: "jquery: create vertical variant of the standard ui.tabs"
date: 2009-02-19
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-19
Hi all, 

(I am bowworing the question from [http://www.sitepoint.com/forums/showthread.php?t=594234](http://www.sitepoint.com/forums/showthread.php?t=594234) since I have the same question:)

I would like to create vertical variant of the standard ui.tabs. In visual terms, I would like to "rotate the basic ui.tabs layout by 90 degrees, clockwise"; the tabs should be on the right, with a maximum width of 50-60px. Basically, I would like to re-create a standard, paper-based, address-book, with each tab having a letter (or a range of letters). 

I've tried a number of variations, but my CSS/jQuery skills obviously fall short of my imagination...  

I'm not necessarily stuck with jQuery -- if someone has a nice example using a different solution, all pointers are greatly appreciated. 

Many thanks in anticipation. 

Tom

---

### Post by rharriso on 2009-02-19
JQuery should have the style guide for that plugin. Have you checked that out yet. If you are just having styling issue I could check it out for you. Can you send me the url of you sandbox?

However, because <li> usually are displayed as block level items it might be easier to roll your own.

I would structure it like

[HTML]
<ul>
 <li>
  <div></div>
 </li>
 <li>
  <div></div>
 </li>
</ul>
[/HTML]

Then on click show hide the appropriate divs.
Generally I don't like to use plugins unless it is for something that would take a long time to develop like the date or color picker or the drag/droppables. For something like this, it might be faster to roll your own, and your file size will probably be much lower. Unless you were using other elements from the ui.

---

### Post by qmqmqm on 2009-02-20
> **rharriso said:**
> JQuery should have the style guide for that plugin. Have you checked that out yet. If you are just having styling issue I could check it out for you. Can you send me the url of you sandbox?

However, because <li> usually are displayed as block level items it might be easier to roll your own.

I would structure it like

[HTML]
<ul>
 <li>
  <div></div>
 </li>
 <li>
  <div></div>
 </li>
</ul>
[/HTML]

Then on click show hide the appropriate divs.
Generally I don't like to use plugins unless it is for something that would take a long time to develop like the date or color picker or the drag/droppables. For something like this, it might be faster to roll your own, and your file size will probably be much lower. Unless you were using other elements from the ui.

Hi rharriso

Thanks very much for your reply. Attached is the html file with jquery libraries. I have isolated the code for the tabs, it's called test tabs.html. I just cannot figure out how to get it to display horizontally...

Thanks a million.

Tom

---

### Post by rharriso on 2009-02-20
hopefully I'll be able to get to it this weekend. I should be able too. I'll let you know as soon as I do.

---

### Post by rharriso on 2009-02-21
Ok man here you go, there isn't much style to this one, but this is the basic .css and js you would need for what you are talking about. let me know if you need any help

---

### Post by qmqmqm on 2009-02-21
Hey Rharriso

Thanks so much for your help!

I have re-included this following function into the html file to make the page initially display the first tab instead of displaying nothing:

		<script type="text/javascript">
			$(function(){

				// Accordion
				$("#accordion").accordion({ header: "h3" });
	
				// Tabs
				$('#tabs').tabs();
	

				// Dialog			
				$('#dialog').dialog({
					autoOpen: false,
					width: 600,
					buttons: {
						"Ok": function() { 
							$(this).dialog("close"); 
						}, 
						"Cancel": function() { 
							$(this).dialog("close"); 
						} 
					}
				});
				
				// Dialog Link
				$('#dialog_link').click(function(){
					$('#dialog').dialog('open');
					return false;
				})
				.hover(
					function() { $(this).addClass('ui-hover-state'); }, 
					function() { $(this).removeClass('ui-hover-state'); }
				);

				// Datepicker
				$('#datepicker').datepicker({
					inline: true
				});
				
				// Slider
				$('#slider').slider({
					range: true
				});

			});
		</script>

Have a great day!

Tom

---

