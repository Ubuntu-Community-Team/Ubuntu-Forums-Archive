---
title: "What's wrong with my RoR custom tag logic?"
date: 2008-03-24
forum: Programming Talk
---

### Post by moephan on 2008-03-24
I would like my web site to include a user's community rating along with their user name whenever their user name is displayed. Since I show the user name in many places on the site, it seemed that a custom tag would be a natural solution. This is my first custom tag in RoR.

First, I created the following method in application_helper.rb:
```

	def user_tag()
		concat("output goes here")
	end

```

Then I try to use that in one of my layouts:
```

	<%= user_tag %>

```

But then I get the following error:
```

wrong number of arguments (1 for 2)

Extracted source (around line #52):

49:  		<TD>
50:  			<DIV id="userControl">
51: 				<% if @signed_in %>
52: 					<%= user_tag %>
53: 					<SPAN class="sentenceText">signed in as <SPAN class="emphasis"><%= @username %>(<%= @user.rating %>)</SPAN></SPAN>
54: 					<FORM action="/user/signout" method="post">
55: 						<BUTTON type="submit" class="secondary">Sign Out</BUTTON>


```
I've tried adding parameters to the definition, but I always end up with the wrong number of arguments.

Does anyone know what I am doing wrong? Thanks.

Cheers, Rick

---

### Post by skeeterbug on 2008-03-24
Your problem isn't the RHTML. The problem is how you use concat.

[http://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison]("http://www.techotopia.com/index.php/Ruby_String_Concatenation_and_Comparison")


```

 def user_tag()
   "output goes ".concat("here")
 end

```

```

<%= user_tag() %>

```

Works fine for me.

---

### Post by moephan on 2008-03-24
Actually, that whole concat thing was totally unnecessary. The sample I was using was a little confusing. So often things in RoR turn out way easier than I was expecting.

Cheers, Rick

---

