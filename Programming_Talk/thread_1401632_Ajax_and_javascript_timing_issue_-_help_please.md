---
title: "Ajax and javascript timing issue - help please"
date: 2010-02-08
forum: Programming Talk
---

### Post by meastwood on 2010-02-08
Am using jquery.

I simply use load() to update the current page with content from another page. I then run a function to modify a few dom elements.

Everything works if I stick an alert("..") in the called function.  When I remove the alert() the dom elements remain unchanged.

I've tried using setTimeout(called function, delay).
I've tried using a wrapper function to call the load() and dom modifying function separately - still requires an alert() in either function to work.

Because things work with alert() I think this is a timing issue - browser has yet to render the loaded dom elements before the second function is called.

```
function ajaxIt(tag_url) {
                        get_file(tag_url);
                        local_links();
  }

function get_file(tag_url) {
                        var tag_and_url = tag_url.split(",");
                        $(tag_and_url[0]).load(tag_and_url[1]+' .contents');
                        //alert("done")    will work
}

function local_links() {
                       // alert("called")   will work
                       $('.local').click(function () {
                               var tgt = $(this).attr('href');
                               var off = $(tgt).offset();
                               var x = off.left;
                               var y = off.top - 190;
                               if ( x != 99 ) {
                                  $(tgt).offset({ top:y, left: 99 }); }
                               $(tgt).scrollTo(1500); });
}

Either //alert() when uncommented will result in the desire result
```

---

### Post by CyberJack on 2010-02-08
You perform a ajax task in one function and change the added content in another function.
Since javascript does not wait for each ajax request to end, you have the timing issue.

I guess you need to use the callback functionality to make this work.

Try this:
```

function ajaxIt(tag_url)
{
	get_file(tag_url);
}

function get_file(tag_url)
{
	var tag_and_url = tag_url.split(",");
	$(tag_and_url[0]).load( tag_and_url[1]+' .contents', function() {
		local_links();
	});
}

function local_links()
{
	$('.local').click(function() {
		var tgt = $(this).attr('href');
		var off = $(tgt).offset();
		var x = off.left;
		var y = off.top - 190;
		if ( x != 99 )
		{
			$(tgt).offset({ top:y, left: 99 });
		}
		$(tgt).scrollTo(1500);
	});
}

```

---

### Post by meastwood on 2010-02-08
dank u well cyberjack -

could have sworn I did that from the outset...  anyway works fine now.  Simplified to -

```
function ajaxIt(tag_url) {
                        var tag_and_url = tag_url.split(",");
                        $(tag_and_url[0]).load(tag_and_url[1],'', function () {
                              $('div').removeClass('wrap_1_no_js wrap_3_no_js gap_no_js');
                              local_links();});
                          }
```

Thanks.

---

