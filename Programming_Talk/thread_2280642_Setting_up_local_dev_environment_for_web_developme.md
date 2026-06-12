---
title: "Setting up local dev environment for web development"
date: 2015-06-01
forum: Programming Talk
---

### Post by dreamsorcerer2 on 2015-06-01
I'm trying to setup a local dev environment for web development, so I can work on a variety of websites locally, these will be WordPress websites.

I'm stuck trying to configure Apache correctly. So, I was wondering if anybody could help me set this up. While I am currently using Apache I don't mind using something else if it is easier to setup.

What I would like is to be able to access a list of projects in ~/Projects/ when accessing, say mylocalenvironment.com. This much I can manage by simply setting the DocumentRoot to this path.

But, then if I navigate to the website index of any of these projects I am presented with a blank page, and I am unsure of how to get this working correctly.

Additionally, it would be good if ~/Projects/project-name/ redirected to ~/Projects/project-name/wordpress/.

As a number of projects will be added over time, I would like this to work without needing to add additional config files for each project.

---

### Post by corti-nico on 2015-06-01
> **dreamsorcerer2 said:**
> I'm trying to setup a local dev environment for web development, so I can work on a variety of websites locally, these will be WordPress websites.

I'm stuck trying to configure Apache correctly. So, I was wondering if anybody could help me set this up. While I am currently using Apache I don't mind using something else if it is easier to setup.

What I would like is to be able to access a list of projects in ~/Projects/ when accessing, say mylocalenvironment.com. This much I can manage by simply setting the DocumentRoot to this path.

But, then if I navigate to the website index of any of these projects I am presented with a blank page, and I am unsure of how to get this working correctly.

Additionally, it would be good if ~/Projects/project-name/ redirected to ~/Projects/project-name/wordpress/.

As a number of projects will be added over time, I would like this to work without needing to add additional config files for each project.
Have you already setted up Apache? If you place a simple index.html file in folder  ~/Projects/project-name/ are you able to see in in browser @url [http://localhost/Projects/project-name/](http://localhost/Projects/project-name/) ?

---

### Post by SeijiSensei on 2015-06-02
> **dreamsorcerer2 said:**
> Additionally, it would be good if ~/Projects/project-name/ redirected to ~/Projects/project-name/wordpress/.

You can use an Alias in the Apache configuration for each site.

```

<VirtualHost *:80>
ServerName development.example.com

Alias /Projects/project-name /home/username/Projects/project-name/wordpress

<Directory /home/username/Projects/project-name/wordpress>
stuff
</Directory>

```

You might prefer to point just /project-name to /home/username/Projects/project-name/wordpress which will give you simple URLs for each project.
```
Alias /project-name /home/username/Projects/project-name/wordpress
```

---

