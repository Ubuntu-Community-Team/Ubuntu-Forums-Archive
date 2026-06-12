---
title: "Ruby: understanding a generated index.rhtml file"
date: 2009-02-03
forum: Programming Talk
---

### Post by thenetduck on 2009-02-03
Hi 

I just used scaffold to generate some ruby code and I have this index.rhtml code right here. I am just trying to understand how the Ruby code knows to call the @ticket class when I never gave it a specific directory? 

Here is the file..

Thanks 

The Net Duck

---

### Post by mikeyv on 2009-02-03
> **thenetduck said:**
> I just used scaffold...
... how the Ruby code knows to call the @ticket class when I never gave it a specific directory?

When you use Rails scaffolding, Rails creates a model, a controller, and views for you.

Have a look at your app/models directory. You should have a ticket.rb model. Similarly, you should have a tickets_controller.rb in your app/controllers.

If you have a look at your tickets_controller.rb file, the scaffold should have put an index function in it for you. Something like:

```

def index
  @tickets = Ticket.find(:all)
  ...
end
```

That line tells Active Record to query the database for all tickets using the Ticket model and assign them to the @tickets variable, which is then available to your index view.

---

