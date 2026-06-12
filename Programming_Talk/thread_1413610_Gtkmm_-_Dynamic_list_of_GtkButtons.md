---
title: "Gtkmm - Dynamic list of Gtk::Buttons"
date: 2010-02-22
forum: Programming Talk
---

### Post by PaulM1985 on 2010-02-22
Hi

I am iterating over a list of strings.  Creating a button which has the name of the string.  Then want to add these buttons to my VBox.  My NavPanel inherits from VBox.  Below is the method I wanted to use:

```

void
NavPanel::DisplayButtons() {

	// Remove all buttons from the user interface
	std::list<Gtk::Button>::iterator buttonListIter;
	for (buttonListIter = m_SubPathButtons.begin(); 
					buttonListIter != m_SubPathButtons.end(); 
					buttonListIter++) {

		remove(*buttonListIter);
	}

	// Remove the buttons from the button list
	m_SubPathButtons.clear();

	// Create all of the buttons for the strings and add the
	// action listeners
	std::list<std::string>::iterator it;
	for (it = m_SubPaths.begin(); it != m_SubPaths.end(); it++) {


		std::string buttonName(it->substr(it->find_last_of("/") + 1));
		Gtk::Button aButton(buttonName);

std::cout << "in here and adding the button " << buttonName << std::endl;
		aButton.signal_clicked().connect(sigc::bind<-1, std::string>(
              sigc::mem_fun(*this, &NavPanel::ProcessButton), buttonName));

		m_SubPathButtons.push_back(aButton);
		pack_start(aButton);
	}

	show_all_children();
}

```

The problems I have are that I can't store aButton in m_SubPathButtons (a std::list<Gtk::Button>) because the compiler says that Gtk::Button::Button(const Gtk::Button &) is private.  When I remove this line and just use the pack_start(aButton), these buttons aren't displayed, which I am assuming is because they have been destroyed after moving out of the for-loop.

Does anyone know how I would be able to dynamically add buttons to a VBox?  I haven't been able to find anything on Google.

Paul

---

