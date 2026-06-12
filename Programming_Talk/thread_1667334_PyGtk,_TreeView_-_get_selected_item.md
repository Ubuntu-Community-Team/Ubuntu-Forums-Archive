---
title: "PyGtk, TreeView - get selected item"
date: 2011-01-14
forum: Programming Talk
---

### Post by again617 on 2011-01-14
I am making a simple project manager tool.  The project has items and tasks, and these may have subtasks.  I am using the tree view to display this information.

I am able to get the gtk.TreeIter of the selected object and I am able to get the value of this item (which in my case is the task name).  But my problem is that this value is not necessarily unique so I cannot look up the task information based only on this value.

Here is a screenshot of the current state with red circles around the offending values:
[IMG]http://ploader.net/files/9080ec44932c1c6b7b40c3a8eb1f3c76.png[/IMG]

What are my options going forward?  Should I just ensure that the task names are unique?  I'd rather not go this route.

Thanks for any help you can offer.  If I have been unclear please tell me where so I can clarify.


p.s. 

The code for when a tree view item is clicked on and the value is printed to console is here:
```

tree_sel = self.tree_view.get_selection()
(tm, ti) = tree_sel.get_selected()
print(tm.get_value(ti, 0)

```

---

### Post by Tony Flury on 2011-01-15
Clearly you need a unique id of some form - what is wrong with generating a unique task number - start at 0 and add one for each task and sub-task created - and never decrement it. Store the Task id with the details - you don't have to display it - and use that.

---

### Post by again617 on 2011-01-15
> **Tony Flury said:**
> Clearly you need a unique id of some form - what is wrong with generating a unique task number - start at 0 and add one for each task and sub-task created - and never decrement it. Store the Task id with the details - you don't have to display it - and use that.

In this case, I have a class called "Task" and it contains the parameters key, name and list of tasks.  Key is unique.  I have a list of these Tasks and I loop through this list (recursively) adding each task to the tree.

```

def add_task_list(self, task_list, parent_item = None):
   if task_list is not None:
      for task in task_list:
         new_parent_item = self.treestore.append(
            parent_item, [task.name])
         self.add_task_list(
            task.taskList, new_parent_item)

```

What I'm wondering is how to associate this key with the item that I'm adding to the tree so that I can later retrieve this key value when a tree item is clicked on.

Thanks for replying.

---

### Post by moephan on 2011-01-17
To associate the key with the data, simply include the key in the list of data that you append, so instead of just [task.name] append [task.name,key]. But you don't create a column to display the key. Then when you get value, use model.get_value(treeiter, 1). The "1" indexes to the second value in the list, which is your key.

---

### Post by again617 on 2011-01-17
> **moephan said:**
> To associate the key with the data, simply include the key in the list of data that you append, so instead of just [task.name] append [task.name,key]. But you don't create a column to display the key. Then when you get value, use model.get_value(treeiter, 1). The "1" indexes to the second value in the list, which is your key.
Thanks!  That was just the information that I was looking for.

---

