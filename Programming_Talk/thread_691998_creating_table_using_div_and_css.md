---
title: "creating table using div and css"
date: 2008-02-09
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-02-09
Hi,

I'm trying to make a table inside my page by using div and css. I could do this simple task in one minute by using tables, but based on my readings I noticed that using table is not recommended nowadays, so I'm going to use div and css.

What I need to create is a very simple two column table. The table has 8 rows. The left column should contain an image of width 50px and the right one will have a text. Text align for the text should be right to left and direction is from right to left. 

Right now I'm using the following code with no luck. FF, Opera and IE are showing it in the same way. Even sometimes each row behavior is different from each other in all three browsers that I tested. Sometimes text goes to the bottom of the row.

Here is my code:

[PHP]
<div id="video_container">
        // Here loop starts
			<div id="video_row">
				<div id="video_image">
					<img src="video/image/{$img}" />
				</div>
				<div id="video_info">
						Hi, How are you?
				</div>
				
			</div>
	// Here loop ends
</div>
[/PHP]

And here is the CSS:

[PHP]
#video_container {
	font-family: tahoma;
	padding:3px;
	text-align:right;
	direction:ltr;
	margin-top:10px;
	height:100%;
	width:100%;
}

#video_row {
	display:table-row;
	text-align:right;
	width:100%;
	border-style:dotted;
}

#video_row:hover {
	background-color:red;
}

#video_image {
	text-align:right;
	display:table-cell;
	float:left;
	width:50px;
	vertical-align:top;
	margin-bottom:15px;
}

#video_image img:hover {
	opacity:0.8;
}

#video_info {
	float:left;
	margin-left:250px;
	display:table-cell;
	text-align:right;
	font-weight:bold;
	direction:rtl;
	border-style:solid;
}
[/PHP]

Any idea how to get this working without using tables?

---

### Post by CptPicard on 2008-02-09
Tables are not recommended for doing *layout*, but for tabular presentation, you should use... tables. :)

I'll leave it up to you to consider which it is you're trying to achieve...

---

### Post by mohtasham1983 on 2008-02-09
My table is not used much for tabular presentation.

If you look at digg.com page source, you notice they don't use any table at all. Their famous content is made from div elements. There should be something in their mind that they didn't use table. I'm also trying to use their method, even though it's extremely hard.

---

