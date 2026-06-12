---
title: "Dockable (Grouped) Windows - Where to start?"
date: 2010-06-29
forum: Programming Talk
---

### Post by mzalewski on 2010-06-29
I'm fairly new to linux - I switched to Ubuntu about 3 months ago and  doubt I will ever go back to Windows.

I've been looking for a  plugin to dock windows, and I have found a few tiling managers and  compiz plugins that are about half-way there but not quite what I'm  looking for.

See this screenshot for an example (No negative MS  comments please) :
[http://www.infoq.com/resource/news/2009  ... 2010UI.png]("http://www.infoq.com/resource/news/2009/02/VisualStudio2010-WPF/en/resources/VS2010UI.png")

I am a VS developer and find the UI  to work very well. It's fast, allows me to customise what windows are  displayed and where - and it's something that I think can be applied to  standard OS window management. I know there's a lot of anti-MS people around, but if a UI works well then surely it can be  improved and put to good use in any environment.

I've seen the  compiz grid plugin, and thought this might be a good starting point -  The problem is that I basically want to select windows to reparent into a  dockable workspace, and then change the window decoration based on  where they are positioned. For example, I might have Firefox set up as  my main window and on the upper right have 3 tabbed terminals, lower  right GEdit.
The tabbed terminals and GEdit sections will need to  have window decorations replaced with a more dock-like decoration  (smaller in size, basic Close and Pin/Unpin icon). The terminals should  also have a set of tabs displayed underneath which allow the user to  switch between terminal instances.

I would also like the top of  the screen to show a maximised window decoration that contains the  firefox title (full width, even though the firefox window will only take  up about 75% width in this example)

My questions are:
Where should I start - can/should this be done with a compiz plugin? I'm  using the gtk-decorator, and would like to use the theme colours as much  as possible - will I need to modify the decorator since I'll be modifying the  window decoration for certain windows?
Can I reparent window content? I thought maybe I  could create a top-level window that rehosts all these windows and sets  up the decorations.
Or can I draw window decorations without an  actual window? Then I could simply remove the window decoration from  firefox and position it where I like.

I have spent a few hours going  through the source code of various plugins and components, but still  don't have a good idea of where to start. 

Any help would be  appreciated

Thanks
Matthew

---

