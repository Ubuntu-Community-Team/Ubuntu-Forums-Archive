---
title: "[SOLVED] Ruby object not passed?"
date: 2007-07-13
forum: Programming Talk
---

### Post by Das Oracle on 2007-07-13
I am playing with partials in RoR and I am getting a nil object passed. Any help would be greatly appreciated.  Here is the partial: named _classified

```
<li><%= link_to classified.title, {:action => 'show', :id => classified.id} -%>
	<small><%= link_to 'Edit', {:action => 'edit', :id => classified.id} %></small>
	<small><%= link_to "Delete", {:action => 'delete', :id => classified.id}, :confirm => "Are you sure you want to delete this item?" %></small>
</li>
```

here is where the partial is called: (different file)

```
	<ul id="classifieds">
		<%= render :partial => 'classified', :collection => @classifieds %>
	</ul>
```

and this is where the error occurs (a third different file) 

```
<h1><%= @classified.title %></h1>
```

now the partial is called by the second code block, and results are displayed by the :partial and when i click on any of the links displayed i get a nil error when @classified.title is called. any help would be great. thanks

---

### Post by Das Oracle on 2007-07-13
I fixed it, my problem was i forgot to put a show method in the classified controller

---

