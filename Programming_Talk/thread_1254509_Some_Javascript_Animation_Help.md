---
title: "Some Javascript Animation Help"
date: 2009-08-31
forum: Programming Talk
---

### Post by Beezleray on 2009-08-31
Hey,
I'm using jQuery and I have this webpage, what I want is to have in the background little clouds just floating from left to right (or right to left) across the screen. And once they hit an edge of the screen they "loop" over to the other side.

What I have now is a script that moves the cloud around in the background but randomly, both horizontally and vertically:

```
$(document).ready(function(){
			var floater = function(){
         			$('#cloud').animate( {'marginTop' (Math.random() * $(window).height())
                                 + 'px','marginLeft':(Math.random() * 
                                 $(window).width()) - 50 + 'px'},
			         2000,'linear',function(){
                		          setTimeout(floater,100);
         			});
			}
			floater();
		});
```

I can't figure out how to set it so the could img randomly picks a starting point (any where width-wise, but above the footer height-wise) and move only right to left, not in all four directions. I thought if I set the marginTop value to a static number that it would just move along that line but that just breaks the code and it wont move at all.

Any help would be great!
Thanks

---

### Post by Mirge on 2009-08-31
> **Beezleray said:**
> Hey,
I'm using jQuery and I have this webpage, what I want is to have in the background little clouds just floating from left to right (or right to left) across the screen. And once they hit an edge of the screen they "loop" over to the other side.

What I have now is a script that moves the cloud around in the background but randomly, both horizontally and vertically:

```
$(document).ready(function(){
            var floater = function(){
                     $('#cloud').animate( {'marginTop' (Math.random() * $(window).height())
                                 + 'px','marginLeft':(Math.random() * 
                                 $(window).width()) - 50 + 'px'},
                     2000,'linear',function(){
                                  setTimeout(floater,100);
                     });
            }
            floater();
        });
```I can't figure out how to set it so the could img randomly picks a starting point (any where width-wise, but above the footer height-wise) and move only right to left, not in all four directions. I thought if I set the marginTop value to a static number that it would just move along that line but that just breaks the code and it wont move at all.

Any help would be great!
Thanks

Could you post a link to a page where it's in use? Firebug is tremendously helpful in these situations.

Also, the fact that you have a function named "floater" is awesome :lolflag:

---

### Post by Beezleray on 2009-08-31
I don't have a way to show you it, but looking around I found [this example]("http://www.zachstronaut.com/lab/parallaxsky/parallax.php") which is exactly what I want, so I started messing around with the code he was using (which is in jquery lucky enough).

So the code I have now is this:

```
$(document).ready(function() {
			$('#cloud').data('x',0);

			setInterval(floater, 100);
		});
		
		function floater() {
				$('#cloud').data('x', $('#cloud').data('x') + 1 % 600).css('background-position', $('#cloud').data('x') + 'px 0');
		}
```

Which is a little confusing to me but I get the jist of it. Running it, Firebug shows that the background-position of cloud is increasing rapidly but the image on the site itself doesn't move at all (it also just keeps increasing, but thats something to figure out later). Thats weird right?

---

