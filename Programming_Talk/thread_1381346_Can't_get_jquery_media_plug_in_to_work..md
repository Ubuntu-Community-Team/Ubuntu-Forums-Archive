---
title: "Can't get jquery media plug in to work."
date: 2010-01-14
forum: Programming Talk
---

### Post by kapi on 2010-01-14
Have tried and seem to be at a loss.

don't knpw what i'm doing wrong but when I try to link/ embedd a mpeg r anything else in to a script I get page not found.

Any ideas?

<script src="js/jquery-1.3.2.min.js" type="text/javascript"></script>
<script src="js/jquery.media.js" type="text/javascript"></script>
<script src="js/mediaplayer-viral/player-viral.swf"></script>

 
<script type="text/javascript">

//fire once the dom is ready
 $(document).ready(function() //so when doc is loaded
 {
	 	$("a.media").media();
  	
 });


</script>
<title>Jquery -embedding media</title>
</head>

	<body>
	<h1>Media types</h1>
	<a class="media" href="test.mpeg">movie</a>
	
	</body>

---

