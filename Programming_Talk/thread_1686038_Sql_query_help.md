---
title: "Sql query help"
date: 2011-02-11
forum: Programming Talk
---

### Post by PetePete on 2011-02-11
Just can't seem to get this one.
I've the following tables (changed names for simplicity sake)

[Recipe]
-id, Name

[Ingredient]
-id Name

[RecipeToIngredient] (Many to Many)
-RecipeID
-IngredientID

i'm trying to get a query which returns me all the recipes which have a maximum of 2 missing ingredients.

I've written the following statement, but it only returns recipes which have a Minimum of 2 ingredients in the list (1,2). so a recipe may have 10 ingredients and we only have 2.
```

 SELECT    *     FROM recipie WHERE ID IN (
SELECT RecipieID FROM RecipieToIngrediants
                           WHERE IngrediantID IN (1,2)
                           GROUP BY recipieID
                           HAVING COUNT(recipieID)>=2
                      )

```

Thanks,

---

### Post by Some Penguin on 2011-02-12
I don't know what you mean by "missing ingredient".

```

SELECT distinct(RecipeID) FROM rtoi T1 WHERE
(SELECT count(distinct(IngredientID)) FROM rtoi T2 
 WHERE T1.RecipeID = T2.RecipeID AND
       T2.IngredientID NOT IN (SELECT id from Ingredient)) >= 2

```

would look for recipe ids with 2+ distinct ingredient ids which aren't in your official ingredient list, methinks.

---

