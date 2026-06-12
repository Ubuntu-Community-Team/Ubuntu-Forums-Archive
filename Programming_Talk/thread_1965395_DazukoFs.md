---
title: "DazukoFs"
date: 2012-04-25
forum: Programming Talk
---

### Post by emiller12345 on 2012-04-25
I would like to try and get this module working with the linux 3.x kernel but it will take some updating. I'm hoping that it will not be that difficult and have started working on a patch to correct this.

the patch below allows the dazukofs program to compile on the 3.0.17 kernel, but does not work as expected.  I believe the problem is probably in the dazukofs_d_compare function, mainly because I wasn't entirely sure how to convert it.

testing the system with an eicar test file did not result in detection.

If anyone has an idea what I could try, please let me know.

```
diff -r -u a/dazukofs-3.1.4/dentry.c b/dazukofs-3.1.4/dentry.c
--- a/dazukofs-3.1.4/dentry.c    2010-05-30 06:58:04.000000000 -0400
+++ b/dazukofs-3.1.4/dentry.c    2012-04-25 16:14:06.517056528 -0400
@@ -116,10 +116,11 @@
 {
     struct dentry *lower_dentry = get_lower_dentry(dentry);
 
+    struct inode *lower_inode = get_lower_inode(dentry);
     if (!lower_dentry->d_op || !lower_dentry->d_op->d_hash)
         return 0;
 
-    return lower_dentry->d_op->d_hash(lower_dentry, name);
+    return lower_dentry->d_op->d_hash(lower_dentry, lower_inode, name);
 }
 
 /**
@@ -160,8 +161,9 @@
 {
     struct dentry *lower_dentry = get_lower_dentry(dentry);
 
+    struct inode  *lower_inode  = get_lower_inode(dentry);
     if (lower_dentry->d_op && lower_dentry->d_op->d_compare)
-        return lower_dentry->d_op->d_compare(lower_dentry, a, b);
+        return lower_dentry->d_op->d_compare(lower_dentry, lower_inode, NULL, NULL, 0, a, b);
 
     if (a->len != b->len)
         return 1;
diff -r -u a/dazukofs-3.1.4/super.c b/dazukofs-3.1.4/super.c
--- a/dazukofs-3.1.4/super.c    2010-10-16 12:03:57.000000000 -0400
+++ b/dazukofs-3.1.4/super.c    2012-04-25 14:39:10.701203398 -0400
@@ -160,7 +160,7 @@
     int err;
 
     memset(&nd, 0, sizeof(struct nameidata));
-    err = path_lookup(dev_name, LOOKUP_FOLLOW | LOOKUP_DIRECTORY, &nd);
+    err = kern_path(dev_name, LOOKUP_FOLLOW | LOOKUP_DIRECTORY, &nd);
     if (err)
         return err;
 
@@ -206,7 +206,7 @@
     struct super_block *sb;
     int err;
 
-    err = get_sb_nodev(fs_type, flags, data, dazukofs_fill_super, mnt);
+    err = mount_nodev(fs_type, flags, data, dazukofs_fill_super);
     if (err)
         goto out;
 
@@ -306,7 +306,7 @@
 static struct file_system_type dazukofs_fs_type = {
     .owner        = THIS_MODULE,
     .name        = "dazukofs",
-    .get_sb        = dazukofs_get_sb,
+    .mount        = dazukofs_get_sb,
     /*
      * XXX: We are using kill_anon_super() instead of my own function.
      *      Is this OK?
```

---

