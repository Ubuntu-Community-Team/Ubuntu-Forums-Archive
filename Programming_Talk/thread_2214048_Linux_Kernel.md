---
title: "Linux Kernel"
date: 2014-03-30
forum: Programming Talk
---

### Post by Muhammad_Nouman on 2014-03-30
```
static void insertion (char value[]) {
        struct AVLTree_Node *bf, *parent_bf, *subtree, *temp;
        struct AVLTree_Node *current, *parent, *newnode, *ptr;
        int res = 0,i=0 ,num=100, compareLimit = 100; 
        char link_dir[32];


        if (!root) {
                root = createNode(value);
                return;
        }


        bf = parent_bf;
        parent_bf = root;
        // find the location for inserting the new node
        for (current = root; current != NULL; ptr = current, current =current->link[res]) {
             
                num = strcmp(value,current->data);
                if (num == 0) {
                        printk(KERN_INFO "Cannot insert duplicates!!\n");
                        return;
                }
                int result = strncmp(value,current->data, compareLimit);
                if(result > 0) 
                        res = 1;  
                else if(result <= 0) 
                        res =0;
                parent = current;


                if (current->bfactor != 0) {
                        bf = current;
                        parent_bf = ptr;
                        i = 0;
                }
                link_dir[i++] = res;
        }
        // create the new node 
        newnode = createNode(value);
        parent->link[res] = newnode;
        res = link_dir[i = 0];
        // updating the height balance after insertion 
        for (current = bf; current != newnode; res = link_dir[++i]) {
                if (res == 0)
                        current->bfactor--;
                else
                        current->bfactor++;
                current = current->link[res];
        }


        // right sub-tree 
        if (bf->bfactor == 2) {
                printk(KERN_INFO "bfactor = 2\n");
                temp = bf->link[1];
                if (temp->bfactor == 1) {                   
                        subtree = temp;
                        bf->link[1] = temp->link[0];
                        temp->link[0] = bf;
                        temp->bfactor = bf->bfactor = 0;
                } else {
                        subtree = temp->link[0];
                        temp->link[0] = subtree->link[1];
                        subtree->link[1] = temp;
                        bf->link[1] = subtree->link[0];
                        subtree->link[0] = bf;
                        // update balance factors 
                        if (subtree->bfactor == -1) {
                                bf->bfactor = 0;
                                temp->bfactor = 1;
                        } else if (subtree->bfactor == 0) {
                                bf->bfactor = 0;
                                temp->bfactor = 0;
                        } else if (subtree->bfactor == 1) {
                                bf->bfactor = -1;
                                temp->bfactor = 0;
                        }
                        subtree->bfactor = 0;
                }
        // left sub-tree 
        } else if (bf->bfactor == -2) {
                temp = bf->link[0];
                if (temp->bfactor == -1) {
                        
                         // single rotation(SR) right
                    
                        subtree = temp;
                        bf->link[0] = temp->link[1];
                        temp->link[1] = bf;
                        temp->bfactor = bf->bfactor = 0;
                } else {
                        // double rotation - (SR left + SR right)
                         
                        subtree = temp->link[1];
                        temp->link[1] = subtree->link[0];
                        subtree->link[0] = temp;
                        bf->link[0] = subtree->link[1];
                        subtree->link[1] = bf;
                        // update balance factors 
                        if (subtree->bfactor == -1) {
                                bf->bfactor = 1;
                                temp->bfactor = 0;
                        } else if (subtree->bfactor == 0) {
                                bf->bfactor = 0;
                                temp->bfactor = 0;
                        } else if (subtree->bfactor == 1) {
                                bf->bfactor = 0;
                                temp->bfactor = -1;
                        }
                        subtree->bfactor = 0;
                }
        } else {
                return;
        }


        if (bf == root) {
                root = subtree;
                return;
        }
        if (bf != parent_bf->link[0]) {
                parent_bf->link[1] = subtree;
        } else {
                parent_bf->link[0] = subtree;
        }
        return;
}

```

This is a function of my code. It is an insertion function of AVL tree. It works fine when I tried to compile using c but it did'nt work
when i tried to compile as a kernel module. It shows the same error on these lines

for (current = root; current != NULL; ptr = current) {
current = current->link[res];
for (current = bf; current != newnode; res = link_dir[++i]) {

error: lvalue required as left operand of assignment
I am using kernel version 2.6.32-24-generic

How can I fix this??

---

### Post by trent.josephsen on 2014-03-30
Those first two lines don't appear in the given source code listing, so either you are misrepresenting the error message, or the code you're compiling is different from the code you posted. Please copy and paste the actual error output when compiling the code from the OP, along with the exact commands you used to compile it, in order for us to help you.

---

### Post by ofnuts on 2014-03-30
Looks like one of the kernel header files is defining "current" (macro?).

---

### Post by Muhammad_Nouman on 2014-03-31
Yes sir, you are right. It works when I replaced all the current variables by some other name. Thanks

---

