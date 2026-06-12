---
title: "C# - Event handler can't access parent function objects."
date: 2009-10-21
forum: Programming Talk
---

### Post by OpenGuard on 2009-10-21
As simple as that .. how do I make global objects ? Once you click on the list item, I need it to load appropriate description, but so far, seems impossible.

```
        public void FetchData(string url)
        {
            XmlDocument xDoc = new XmlDocument();
            xDoc.Load(url);
            XmlNodeList title = xDoc.GetElementsByTagName("title");
            XmlNodeList description = xDoc.GetElementsByTagName("description");

            for (int i = 0; i < title.Count; i++)
            {
                lstEntries.Items.Add(title[i].InnerText);
            }

            lstEntries.Click += new System.EventHandler(lstEntries_OnClick);
        }

        private void lstEntries_OnClick(object sender, System.EventArgs e)
        {
            // description array can't be accessed from here
        }
```

---

