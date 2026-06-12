---
title: "[SOLVED] [Python] Problem with Dictionary as Parameter"
date: 2008-07-25
forum: Programming Talk
---

### Post by TreeFinger on 2008-07-25
[php]
class RecipeBook:
	"""The RecipeBook class contains the ingredients needed for foods entered. Ingredients are contained
	inside a nested dictionary. First Key is name of food, second key is the ingredients needed
	for the food.
	"""
	def __init__(self):
		recipes = {}
		return
	def get_recipe(name):
		return self.recipes[name]

	def create(recipe_name, ingredients):
		recipes[recipe_name] = ingredients
[/php]

```

>>> myRecip = RecipeBook()
>>> myRecip.create("cheese_omelet", {"eggs":2, "milk":2, "cheese":1})
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: create() takes exactly 2 arguments (3 given)

```

What is my problem here?

---

### Post by WW on 2008-07-25
You forgot to use **self** in the create() method:
```

   def create(self, recipe_name, ingredients):
        self.recipes[recipe_name] = ingredients

```

By the way, you also forgot the **self** argument in get_recipe().

---

### Post by TreeFinger on 2008-07-25
> **WW said:**
> You forgot to use **self** in the create() method:
```

   def create(self, recipe_name, ingredients):
        self.recipes[recipe_name] = ingredients

```

argh, thank you.

[php]
class RecipeBook:
	"""The RecipeBook class contains the ingredients needed for foods entered. Ingredients are contained
	inside a nested dictionary. First Key is name of food, second key is the ingredients needed
	for the food.
	"""
	def __init__(self):
		self.recipes = {}
		return
	def get_recipe(self, name):
		return self.recipes[name]

	def create(self, recipe_name, ingredients):
		self.recipes[recipe_name] = ingredients
[/php]

---

