---
title: "[jQuery] Dynamic selectors"
date: 2008-12-09
forum: Programming Talk
---

### Post by altonbr on 2008-12-09
I'm looking to implement a toggle for an input-driven form with over 40 elements.

Unfortunately, I don't know how to implement dynamic selectors in jQuery.

For example: I am pulling id's from a DB and am printing them as part of the class name for the toggle switch. When that toggle switch is clicked, I am looking for two corresponding divs to open or close.

Here is what I have:
```

$(document).ready(function()
{
	$('#activate-0').click(function(){
		$('#toggle1-0').slideToggle('slow');
		$('#toggle2-0').slideToggle('slow');
	});
});
```

Statically, this works great, but that '-0' could be any number, such as '-3423425464'. But how do I perform a dynamic selector so that '#activate-3423425464' toggles '#toggle1-3423425464' and '#toggle2-3423425464'?

---

### Post by altonbr on 2008-12-09
I found this article which is quite helpful: [http://blog.paranoidferret.com/index.php/2008/12/02/jquery-tutorial-dynamic-sliding-panels/](http://blog.paranoidferret.com/index.php/2008/12/02/jquery-tutorial-dynamic-sliding-panels/)
but unfortunately my records are not nested in a child/parent format.

```
$(document).ready(function(){

  //Fixes an animation glitch caused by the
  //div's dynamic height.  Need to set the
  //height style so the slide functions work
  //correctly.
  $("div.slideBody").each(function(){
    $(this).css("height", $(this).height() + "px");
    });

  //hook the mouseup events to each header
  $("div.slidePanel").children(
    "div.slideHeader").mouseup(function(){
 
    //find the body whose header was clicked
    var body = $(this).parent().children("div.slideBody");

    //slide the panel
    if(body.is(":hidden"))
      body.slideDown();
    else
      body.slideUp();
  });
});
```

Is there any way I can do this dynamically with numbers?

---

### Post by mssever on 2008-12-09
How about something like this? (pseudocode):
```
ids = get list of IDs in document
regex = /^activate-([0-9]+)/
for id in ids {
    if(id.match(regex)) {
        the_number = id.match(regex).backreference(1)
        $('#activate-'+the_number).click(function(){
            $('#toggle1-'+the_number).slideToggle('slow');
            $('#toggle2-'+the_number).slideToggle('slow');
        })
    }
}
```

---

