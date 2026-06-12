---
title: "Uni Project Starting Point Suggestions?"
date: 2005-11-11
forum: Programming Talk
---

### Post by jbodell on 2005-11-11
Hi All,
I'm at university and have a dissertation to do. The project is to make a website that will display live odds that it has found on various bookmakers' websites. Something along the lines of [www.oddschecker.com](www.oddschecker.com), but with a more specific use. The only way I can get these odds is by picking them out of the html files of the relevant pages on the bookies sites. For example, this is ladbrokes site: 

(START)
<span id="span_ev_210728799">Argentina vs England</span>
</td>			
		<input type="hidden" name="lp_num_220114147" value="5" />
		<input type="hidden" name="lp_den_220114147" value="4" />
                <td onmouseover="" nowrap title="Argentina" onclick="toggle_selection('210728799', '0')" id="sel_210728799_0" class="div_coupon_sel_off">
		<input type="radio" name="ev_210728799" value="220114147">
							<a>5/4</a>
						</td>"
(END)

This is where the bookmaker has displayed the odds 5/4 for Argentina to beat england. The odds for draw and lose are in the same format. Obviously the format is different for different bookmakers sites. I think the way that I will grab these odds will be as follows:

1. Goto Bookmakers Homepage.
2. Find and store all internal links.
3. Open all links, Go back to step 2.
4. Search through html files for relevant odds.
5. Display odds on website.

Given my requirements (I think), my question is - What would be the most suitable language(s), and does anyone have any tips or suggestions to make this a less painful task? 

Any help appreciated, Cheers.

---

### Post by simon w on 2005-11-14
First, I know nothing about bookmakers' websites :p

Search for RSS feeds or anything XML based.  This would make life somewhat easier ;)

Failing that, I'd use PHP to write a generic base class for holding match odds and extend it for each website format and add the required parsing for that site.

Just out of interest, what else do you plan to do with this website?

---

### Post by kanenas.net on 2005-11-14
I must agree with **simon w** ! Php is you language...
Do you want to do something like [this]("http://bet.sport.gr/?date=Previous&sc=kpn")

---

