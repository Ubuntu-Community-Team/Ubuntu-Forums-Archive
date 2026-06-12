---
title: "Multiple Model With remote_form_for"
date: 2010-03-08
forum: Programming Talk
---

### Post by s1300045 on 2010-03-08
Hi everyone,

I am trying to write a form in rails that will submit one form with multiple sources. What am I supposed to do so ruby will loop through each model array? I follow the sample on the Rails Framework but not much luck. Can someone show me how it's supposed to be done? Thanks!

```

  <% remote_form_for([@timeslot, @participant], :url => url_for(:action => create), :update => "list") do |f| %>
  <%= f.label :date_begin, "Date:" %>
  <br />
  <%= f.date_select(:date_begin) %>
  <br />
  <%= submit_tag("Submit") %>
<% end %>




```

---

