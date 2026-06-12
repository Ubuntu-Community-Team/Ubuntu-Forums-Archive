---
title: "RoR Error"
date: 2007-07-04
forum: Programming Talk
---

### Post by Das Oracle on 2007-07-04
Here's my code:

```
class Classified < ActiveRecord::Base
	belongs_to :category
	validates_presence_of :title,
		:message => "cannot be blank. Make your title descriptive"
	validates_presence_of :price
	validates_numericality_of :price,
		:message => "must be a numeric value (no $ signs or decimals)"
	validates_presence_of :location
	validates_presence_of :description
	validates_presence_of :email
	
	protected
		def validate
			   errors.add(:price, "should be a positive value") if price.nil?
				|| price <= 0
		end
	validates_format_of :email, 
	 :with => /^([^@\s]+)@((?:[-a-z0-9]+\.)+[a-z]{2,})$/i	
end
```

and the error i get from such code is found at this site: vesoautomotive.dyndns.org:3000
the site is just a dyndns link to my apache server so please don't think to be spam. 

specifically the error I am getting involves this line of code:

```
		def validate
			   errors.add(:price, "should be a positive value") if price.nil?
				|| price <= 0
		end
```

---

### Post by Modred on 2007-07-05
You can't wrap that statement around to the next line.  It needs to be like this:
```
errors.add(:price, "should be a positive value") if price.nil? || price <= 0
```
Ruby issue more so than Rails.

---

### Post by Das Oracle on 2007-07-05
Ok, thanks. I figured you could have it wrap around at certain points like with commas and (i presumed) logic statements. I was wrong and thanks for proving me so.

---

### Post by avik on 2007-07-05
Actually, you can wrap the statement, but only if it's clear that it's two lines.  There are two ways to do this:

```
errors.add(:price, "should be a positive value") if price.nil? ||
price <= 0
```

The || is on the first line, so Ruby *knows* without a doubt that another line will follow.  Or you can use:

```
errors.add(:price, "should be a positive value") if price.nil? \
|| price <= 0
```

The backslash has the same effect.

But in the end, it's best to keep it in one line.

---

### Post by Modred on 2007-07-05
You learn something new every day.  (Although I'm sure it's in my Rails and/or Ruby books somewhere...)  Good tip.

---

### Post by unixhead on 2007-07-05
It's in Pickaxe book :)

---

### Post by avik on 2007-07-05
> **unixhead said:**
> It's in Pickaxe book :)

[Here's the first edition available online.]("http://www.rubycentral.com/book/index.html")  You can buy the second edition in print only.  :p

---

