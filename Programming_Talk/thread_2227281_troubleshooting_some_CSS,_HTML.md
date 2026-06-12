---
title: "troubleshooting some CSS, HTML"
date: 2014-06-01
forum: Programming Talk
---

### Post by Drone4four on 2014-06-01
For one of my first webdesign projects for fun I am borrowing from a code sample featured in a magazine called, HTML5 and CSS3 Genius Guide.  [Here]("http://www.webdesignermag.co.uk/wp-content/uploads/2013/09/4_New_look_layouts.zip") is a link to the zip file. 

I adapted the base html to prepare to add my own content. [Here]("www.angeles4four.info/who/i/am/h2v5kasdh/index-betasnapshot1jun2014.html") is the webpage I am working on.

Here is my modified HTML file:
```

<!DOCTYPE html>
<html lang="en">
    <head>
		<meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"> 
        <title>Sloping Site with CSS3</title>
	<meta name="robots" content="noindex,nofollow" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
        <link rel="stylesheet" type="text/css" href="css/reset.css" />
        <link rel="stylesheet" type="text/css" href="css/style.css" />
		<link href='http://fonts.googleapis.com/css?family=Armata' rel='stylesheet' type='text/css'>
    </head>
    <body>
        <div class="top-container">
		<header>
		<!-- 			<br /> <br /> <br /> <br /> <br /> <br /> <br /> <br /> <br /> -->
				<center><h1><span> About Mr. Angeles</span></h1></center>
				<!-- <h2>Creating interesting layouts with background images</h2> -->
			</header>
			<section class="container">
				<div class="angle full" data-stretch="img/csgo.jpg">
					<article class="content">
						<h3>Counter-Strike</h3>
						<p>Irrespective according strived jeez a beyond jaguar to in crab some when hey prodigiously hello playfully depending however gosh some hamster slit lion dismounted boundlessly save so hummingbird walrus and earnest amid abnormally however infallibly gawked on incapably in rightly.</p>
						<p>Irrespective according strived jeez a beyond jaguar to in crab some when hey prodigiously hello playfully depending however gosh some hamster slit lion dismounted boundlessly save so hummingbird walrus and earnest amid abnormally however infallibly gawked on incapably in rightly.</p>
					</article>
				</div>
					</article>
				</div>
				<div class="angle">
					<article class="content">
						<h3>transition</h3>
						<p>Irrespective according strived jeez a beyond jaguar to in crab some when hey prodigiously hello playfully depending however gosh some hamster slit lion dismounted boundlessly save so hummingbird walrus and earnest amid abnormally however infallibly gawked on incapably in rightly.</p>
					</article>
				</div>
				<div class="angle full" data-stretch="img/sketchbook4.JPG">
					<article class="content">
						<h3>Art</h3>
						<p>[link to DEV Art profile]</p>
						<p>Stared some luscious grimaced as versus gawkily pitifully emotionally scowled before one buffalo egotistically insane much like maturely fought much overate far hello far unnecessarily much a in abusive much less alas and especially as amazing far freshly broken ouch limpet owl painfully less aboard much suave a untruthfully or one too many. </p>
						<!-- <br /> <br /> <br /> <br /> <br /> <br /> <br /> <br /> <br /> -->
					</article>
				</div>
				<div class="angle">
					<article class="content">
						<h3>transition</h3>
						<p>That guinea in far breezily much far ouch in tardily built above a contumaciously misspelled paid less against realistically unexplainably cuddled this leered fiendishly parrot that haughtily blissful as jaguar raccoon one befell this nonchalantly threw desirably flapped dog some gazelle rabidly since one.</p>
					</article>
				</div>
                               <div class="angle full" data-stretch="img/oldman.jpg">
                                        <article class="content">
                                                <h3>Revolution</h3>
                                                <p>Stared some luscious grimaced as versus gawkily pitifully emotionally scowled before one buffalo egotistically insane much like maturely fought much overate far hello far unnecessarily much a in abusive much less alas and especially as amazing far freshly broken ouch limpet owl painfully less aboard much suave a untruthfully or one too many. </p>
                                        </article>
                                </div>
                                <div class="angle">
                                        <article class="content">
                                                <h3>transition</h3>
                                                <p>That guinea in far breezily much far ouch in tardily built above a contumaciously misspelled paid less against realistically unexplainably cuddled this leered fiendishly parrot that haughtily blissful as jaguar raccoon one befell this nonchalantly threw desirably flapped dog some gazelle rabidly since one.</p>
                                        </article>
                                </div>

                   <div class="angle full" data-stretch="img/tux.png">
                                        <article class="content">
                                                <h3>GNU/Linux</h3>
                                                <p>Stared some luscious grimaced as versus gawkily pitifully emotionally scowled before one buffalo egotistically insane much like maturely fought much overate far hello far unnecessarily much a in abusive much less alas and especially as amazing far freshly broken ouch limpet owl painfully less aboard much suave a untruthfully or one too many. </p>
                                        </article>
                                </div>
                                <div class="angle">
                                        <article class="content">
                                                <h3>transition</h3>
                                                <p>That guinea in far breezily much far ouch in tardily built above a contumaciously misspelled paid less against realistically unexplainably cuddled this leered fiendishly parrot that haughtily blissful as jaguar raccoon one befell this nonchalantly threw desirably flapped dog some gazelle rabidly since one.</p>
                                        </article>
                                </div>



				<div class="angle full" data-stretch="img/indigo.jpg">
					<article class="content">
						<h3>Esoterica and the New Age</h3>
						<p>Less attractive a up jeez ashamed this around this aboard and said below less more this somber shortsightedly until erroneous glibly articulate hey hey much mammoth yikes that grouped mercifully froze under more swelled rhinoceros as the where cardinal that darn goldfinch less greyhound in but this this diligent crud mistakenly, gnashed fled thus one inside.</p>
					</article>
				</div>
				<div class="angle">
					<article class="content">
						<h3>???</h3>
						<p>The centre cannot hold.</p>
						<!-- <p>Darn much after frank much that deer far cagily led close without and smirked wittily complacent much the the overdid well uninspiringly masochistically arbitrarily as less stole howled after thus jeez pithily because the masterfully frailly limply beguilingly less liberal reindeer one less soft lighthearted near in deer hey. </p> -->
					</article>
				</div>

                               <div class="angle full" data-stretch="img/grounded.jpg">
                                        <article class="content">
                                                <h3>Mindfulness</h3>
                                                <p>Less attractive a up jeez ashamed this around this aboard and said below less more this somber shortsightedly until erroneous glibly articulate hey hey much mammoth yikes that grouped mercifully froze under more swelled rhinoceros as the where cardinal that darn goldfinch less greyhound in but this this diligent crud mistakenly, gnashed fled thus one inside.</p>
                                        </article>
                                </div>
                                <div class="angle">
                                        <article class="content">
                                                <h3>Me [ Summary? ] </h3>
                                                <p>Darn much after frank much that deer far cagily led close without and smirked wittily complacent much the the overdid well uninspiringly masochistically arbitrarily as less stole howled after thus jeez pithily because the masterfully frailly limply beguilingly less liberal reindeer one less soft lighthearted near in deer hey. </p>
                                        </article>
                                </div>


			</section>
        </div>
        <script src="js/lib/jquery-1.7.1.min.js"></script>
		<script src="js/jquery.anystretch.min.js"></script>

		<script>
		    $(".full").anystretch();
	    </script>
    </body>
</html>

```

Here is my styles.css which is virtually unchanged from the original:
```

body{
	font-family: Georgia, serif;
	background: #d7d9d9;
	font-weight: 300;
	font-size: 15px;
	color: #091e3d;
	background: url(../img/pulp.gif) repeat;


}
.top-container{
	padding-top: 75px;
	width: 100%;
	position: relative;
	text-align: center;
	background: url(../img/pulp.gif) repeat-x top left;
}
.clr{
	clear: both;
}
.top-container > header{
	padding: 50px 30px 10px 30px;
	margin: 0px 20px 10px 20px;
	position: relative;
	display: block;
	text-shadow: 1px 1px 1px rgba(0,0,0,0.2);
    text-align: left;
}
.top-container > header h1{
	font-family: 'Armata', sans-serif;;
	font-size: 50px;
	line-height: 50px;
	position: relative;
	font-weight: 400;
	color: #fff;
	text-shadow: 1px 1px 1px rgba(0,0,0,0.3);
    padding: 0px 0px 5px 0px;
}
.top-container > header h1 span{
	color: #091e3d;
	text-shadow: 0px 1px 1px rgba(0,0,0,0.3);
}
.top-container > header h2{
	font-size: 16px;
	font-style: italic;
	padding: 0px 0px 15px 0px;
}

/* Media Queries */
@media screen and (max-width: 767px) {
	.top-container > header{
		text-align: center;
	}
}

/*Angles Section*/
.container{
	display: block;
	width: 100%;
	overflow: hidden;
	padding-top: 50px;
}
.angle{
	margin: 0 -50px;
	-webkit-transform-origin: left center;
	-moz-transform-origin: left center;
	-o-transform-origin: left center;
	-ms-transform-origin: left center;
	transform-origin: left center;
}


.angle:nth-child(odd){
	border-top: 16px solid #091e3d;
	-webkit-transform: rotate(5deg);
	-moz-transform: rotate(5deg);
	-o-transform: rotate(5deg);
	-ms-transform: rotate(5deg);
	transform: rotate(5deg);
	margin-top: -200px;
}
.angle:nth-child(even){
	background: #ccc url(../img/pulp.gif) repeat;
	-webkit-transform: rotate(-5deg);
	-moz-transform: rotate(-5deg);
	-o-transform: rotate(-5deg);
	-ms-transform: rotate(-5deg);
	transform: rotate(-5deg);
}
.angle:first-child{
	margin-top: 0px;
}
.content{
	margin: 0 auto;
/* 	background: url(../img/pulp.gif) repeat; */
}

.content h3{
	font-size: 60px;
	position: relative;
	display: inline-block;
	padding: 10px 30px 8px 30px;
	height: 80px;
	line-height: 80px;
	margin-bottom: 20px;
	font-family: 'Armata', sans-serif;
}
.content p{
	width: 75%;
	max-width: 500px;
	margin: 0 auto;
	font-size: 18px;
	line-height: 24px;
	padding-top: 10px;
}

.angle:nth-child(odd) .content{
	-webkit-transform: rotate(-5deg);
	-moz-transform: rotate(-5deg);
	-o-transform: rotate(-5deg);
	-ms-transform: rotate(-5deg);
	transform: rotate(-5deg);
	color: #fff;
	text-shadow: 2px 2px 2px rgba(0,0,0,0.7);
	padding: 130px 100px 250px 100px;
}
.angle:nth-child(even) .content{
	-webkit-transform: rotate(5deg);
	-moz-transform: rotate(5deg);
	-o-transform: rotate(5deg);
	-ms-transform: rotate(5deg);
	transform: rotate(5deg);
	padding: 130px 100px 200px 100px;
}
.angle:nth-child(odd) .content h3{
	color: #fff;
}

/* Media Queries */
@media screen and (max-width: 1010px){
	.content h3{
		font-size: 40px;
	}
}
@media screen and (max-width: 767px) {
	.content h3{
		font-size: 35px;
	}
}
@media screen and (max-width: 400px) {
	.content p{
		width: 95%;
	}
	.angle:nth-child(odd) .content,
	.angle:nth-child(even) .content{
		padding-left:60px;
		padding-right:60px;
		
	}
}

```

I have two questions.

[LIST=1]
[*]All headings throughout my webpage should be centered, as per the <h3> tag in my html file and h3 selector in my CSS.  But only the first heading (&#8220;Counter Strike&#8221;) is. What is causing this unexpected behavior?  
[*]Also,when you scroll over to the right, the angled images are pointy and there is an ugly gap.  See [here]("http://i.imgur.com/2kVYaps.png"). What is causing the gap on the right margin and seamless and smooth contact with the left margin?
[/LIST]

I had a third question, but I forget now.  It'll come to me.

Thanks for your attention.

---

### Post by Drone4four on 2014-06-01
Aye, I shared this thread with a friend of mine who answered both my questions.

With respect to #1: The alignment of my headings were messed up because I had a duplicate of "</article>	</div>" in the counter-strike section.

With respect to #2: Playing around with the margin values with under the .angle class selector fixed my issue.

---

