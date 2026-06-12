---
title: "GWT + DisclosurePanel + arrows"
date: 2010-07-19
forum: Programming Talk
---

### Post by rlebosse on 2010-07-19
Hi everybody,
I'm trying to change the arrow icons of the GWT disclosure panels. I
made it in a GWT class.

[B]public interface CustomDisclosurePanelImages extends
DisclosurePanelImages
{
public AbstractImagePrototype disclosurePanelClosed();

public AbstractImagePrototype disclosurePanelOpen();
}[/B]
[B]
CustomDisclosurePanelImages cdpi = (CustomDisclosurePanelImages) GWT
.create(CustomDisclosurePanelImages.class);[/B]

However, my DisclosurePanel is created into an XML file. I created it that way.
[B]<ui:image field='disclosurePanelClosed' />
<ui:image field='disclosurePanelOpen' />

<g:HTMLPanel>
<g:disclosurePanel ui:field="sessions" stylePrimaryName='menu'>
<g:header openImage='{disclosurePanelOpen}' closeImage='{disclosurePanelClosed}'>Sessions</g:header>
<g:HTMLPanel>
<ul class='{eres.menu.menuItems}'>
<li>
<g:Anchor ui:field="sessionsTotal" styleName=''>Total</
g:Anchor>
</li>
<li>
<g:Anchor ui:field="sessionsByActivity" styleName=''>by
Activity</g:Anchor>
</li>
</ul>
</g:HTMLPanel>
</g:disclosurePanel>
</g:HTMLPanel>[/B]

When I try to display my page, I've got the following error. Do you know what could be the cause of it? And how I can fix it? Thanks in advance for your help!

**10:29:14.633 [ERROR] [ermin] In <g:header closeImage='{disclosurePanelClosed}' openImage='{disclosurePanelOpen}'> of <g:disclosurePanel stylePrimaryName='menu' ui:field='sessions'>, both openImage and closedImage must be specified, or neither**

---

### Post by torzsmokus on 2011-04-06
close**d**Image will do. just a typo.

---

