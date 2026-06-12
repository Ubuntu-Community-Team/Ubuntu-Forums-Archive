---
title: "Java Treeview"
date: 2011-01-25
forum: Programming Talk
---

### Post by simolokid4 on 2011-01-25
Hi Ubuntuforums,

I'm trying to code a java program together, for use of sharing files with friends n family -> mostly people that can barely check their email.

Now I've gotten a working ftp connection, I get a list with directorys returned, its just my treeview that... wont update.

It somehow keeps the default categories (how do i remove those anyway?, prob call a reset something @ constructor of gui im guessing )

I did actually burn trough 
[http://download.oracle.com/javase/tutorial/uiswing/components/tree.html](http://download.oracle.com/javase/tutorial/uiswing/components/tree.html)

But somehow.. that doesn't work for me. It can be i overlooked something, but I did double check it ;x

Any help is greatly appreciated :)

Kind regards,

Simolokid;

When pushing a specific button:
```

DefaultMutableTreeNode node = new DefaultMutableTreeNode("Personal folders");
        
        DefaultTreeModel top =
            new DefaultTreeModel(node);
        
        

        createNodes(node);
        treeviewThingy = new JTree(top);
```Where createNodes does this:
```

FTP_Connection ftp_conn = new FTP_Connection("host", "username", "pass");
        ArrayList<String> dir_list = new ArrayList<String>();
        
        try {
            dir_list = ftp_conn.listFiles("");
        } catch (SocketException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (IOException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
        for(String dir_naam : dir_list)
        {
            System.out.println(dir_naam + " | dirname from gui method");
            DefaultMutableTreeNode dir = new DefaultMutableTreeNode(new Directory(dir_naam));
            node.add(dir);                        
        }

```If you need more info feel free to ask.. I'm sure its just a silly typo somewhere >.<

---

