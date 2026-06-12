---
title: "Help me find this memory leak (Python/Pygtk)"
date: 2008-02-25
forum: Programming Talk
---

### Post by imdano on 2008-02-25
(edit: I probably should have added pygtk to the thread title as well, since that's where I think problem is originating.)

Hi,

I've been trying to figure out where this memory leak is originating from for a couple of days now and it's starting to drive me nuts.  I figured I'd let some other people take a look at it and see if anyone spots a circular reference or anything else I'm missing.

The file itself is pretty huge (almost 1800 lines) so I'm going to try to stick to just the relevant parts.  If someone wants the whole thing to test it I can tell you where to get it and how to install and all that.

So, the way it works is gui.py creates a bunch of PrettyNetworkEntry objects when it populates the list of currently available wireless/wired networks.  Then when the "Refresh" button gets pushed, it empties the list of networks that's already there, destroys the objects in there, and repopulates the list.  The problem is that destroying the PrettyNetworkEntry objects isn't freeing up any memory.  If there are a lot of wireless networks around, this causes memory usage to climb up pretty quickly (~.4-.7MB per refresh).

Here is what I think is the relevant code for the NetworkEntry classes
[php]class PrettyNetworkEntry(gtk.HBox):
    """ Adds an image and a connect button to a NetworkEntry. """
    def __init__(self, expander):
        gtk.HBox.__init__(self)
        # Add the stuff to the hbox (self)
        self.expander = expander
        self.expander.show()
        self.expander.higherLevel = self  # Do this so that the expander can access the stuff inside me
        self.tempVBox = gtk.VBox(False, 1)
        self.tempVBox.show()
        self.connectButton = gtk.Button(stock=gtk.STOCK_CONNECT)
        connect_hbox = gtk.HBox(False, 2)
        connect_hbox.pack_start(self.connectButton, False, False)
        #connect_hbox.pack_start(self.expander.scriptButton, False, False)
        #connect_hbox.pack_start(self.expander.advancedButton, False, False)
        connect_hbox.show()
        self.tempVBox.pack_start(self.expander, fill=False, expand=False)
        self.tempVBox.pack_start(connect_hbox, fill=False, expand=False)
        self.pack_end(self.tempVBox)
        #self.expander.scriptButton.show()
        #self.expander.advancedButton.show()
        self.netdes = self.connect("destroy", self.destroy_event)
        
    def destroy_event(self, *args):
        self.disconnect(self.netdes)
        self.expander.higherLevel = None
        self.expander.destroy()
        del self.expander
        super(PrettyNetworkEntry, self).destroy()
        self.destroy()
        print 'DONE'
        

class PrettyWiredNetworkEntry(PrettyNetworkEntry):
    def __init__(self):
        PrettyNetworkEntry.__init__(self, WiredNetworkEntry())
        # Center the picture and pad it a bit
        self.image = gtk.Image()
        self.image.set_alignment(.5, 0)
        self.image.set_size_request(60, -1)
        self.image.set_from_icon_name("network-wired", 6)
        self.image.show()
        self.pack_start(self.image, fill=False, expand=False)
        self.show()
        self.expander.checkEnable()
        self.expander.show()
        self.connectButton.show()
        self.wireddis = self.connect("destroy", self.destroy_event)
        
    def destroy_event(self, *args):
        self.disconnect(self.wireddis)
        self.destroy()


class PrettyWirelessNetworkEntry(PrettyNetworkEntry):
    def __init__(self,networkID):
        PrettyNetworkEntry.__init__(self, WirelessNetworkEntry(networkID))
        self.image = gtk.Image()
        self.image.set_padding(0, 0)
        self.image.set_alignment(.5 ,0)
        self.image.set_size_request(60, -1)
        self.image.set_from_icon_name("network-wired",6)
        self.pack_start(self.image, fill=False, expand=False)
        self.setSignalStrength(wireless.GetWirelessProperty(networkID, 'quality'),
                               wireless.GetWirelessProperty(networkID, 'strength'))
        self.setMACAddress(wireless.GetWirelessProperty(networkID, 'bssid'))
        self.setMode(wireless.GetWirelessProperty(networkID, 'mode'))
        self.setChannel(wireless.GetWirelessProperty(networkID, 'channel'))
        self.setEncryption(wireless.GetWirelessProperty(networkID, 'encryption'),
                           wireless.GetWirelessProperty(networkID, 'encryption_method'))
        self.expander.set_use_markup(True)
        self.expander.set_label(self.expander.essid + "   " + 
                                self.expander.lblEncryption.get_label() + "   "
                                + self.expander.lblStrength.get_label())
        # Show everything
        self.show_all()
        
        self.wifides = self.connect("destroy", self.destroy_event)
        
    def destroy_event(self, *args):
        self.disconnect(self.wifides)
        super(PrettyWirelessNetworkEntry, self).destroy_event()
        self.destroy()[/php]
...
[php]class NetworkEntry(gtk.Expander):
    """ The basis for the entries in the network list. """
    def __init__(self):
        # Make stuff exist, this is pretty long and boring.
        gtk.Expander.__init__(self)
        self.txtIP = LabelEntry(language['ip'])
        self.txtIP.entry.connect('focus-out-event', self.setDefaults)
        self.txtNetmask = LabelEntry(language['netmask'])
        self.txtGateway = LabelEntry(language['gateway'])
        self.txtDNS1 = LabelEntry(language['dns'] + ' ' + language['1'])
        self.txtDNS2 = LabelEntry(language['dns'] + ' ' + language['2'])
        self.txtDNS3 = LabelEntry(language['dns'] + ' ' + language['3'])
        self.vboxTop = gtk.VBox(False, 0)
        
        self.advancedButton = gtk.Button()
        advanced_image = gtk.Image()
        advanced_image.set_from_stock(gtk.STOCK_EDIT, 4)
        advanced_image.set_padding(4, 0)
        self.advancedButton.set_alignment(.5, .5)
        self.advancedButton.set_label(language['advanced_settings'])
        self.advancedButton.set_image(advanced_image)
        
        self.scriptButton = gtk.Button()
        script_image = gtk.Image()
        script_image.set_from_icon_name('execute', 4)
        script_image.set_padding(4, 0)
        self.scriptButton.set_alignment(.5, .5)
        self.scriptButton.set_image(script_image)
        self.scriptButton.set_label(language['scripts'])

        self.checkboxStaticIP = gtk.CheckButton(language['use_static_ip'])
        self.checkboxStaticDNS = gtk.CheckButton(language['use_static_dns'])
        self.checkboxGlobalDNS = gtk.CheckButton(language['use_global_dns'])

        aligner = gtk.Alignment(xscale=1.0)
        aligner.add(self.vboxTop)
        aligner.set_padding(0, 0, 15, 0)
        self.add(aligner)
        
        hboxDNS = gtk.HBox(False, 0)
        hboxDNS.pack_start(self.checkboxStaticDNS)
        hboxDNS.pack_start(self.checkboxGlobalDNS)
        
        self.vboxAdvanced = gtk.VBox(False, 0)
        self.vboxAdvanced.pack_start(self.checkboxStaticIP, fill=False,
                                     expand=False)
        self.vboxAdvanced.pack_start(self.txtIP, fill=False, expand=False)
        self.vboxAdvanced.pack_start(self.txtNetmask, fill=False, expand=False)
        self.vboxAdvanced.pack_start(self.txtGateway, fill=False, expand=False)
        self.vboxAdvanced.pack_start(hboxDNS, fill=False, expand=False)
        self.vboxAdvanced.pack_start(self.txtDNS1, fill=False, expand=False)
        self.vboxAdvanced.pack_start(self.txtDNS2, fill=False, expand=False)
        self.vboxAdvanced.pack_start(self.txtDNS3, fill=False, expand=False)
        
        settings_hbox = gtk.HBox(False, 3)
        settings_hbox.set_border_width(5)
        settings_hbox.pack_start(self.scriptButton, fill=False, expand=False)
        settings_hbox.pack_start(self.advancedButton, fill=False, expand=False)

        self.vboxTop.pack_end(settings_hbox, fill=False, expand=False)

        # Connect the events to the actions
        self.checkboxStaticIP.connect("toggled", self.toggleIPCheckbox)
        self.checkboxStaticDNS.connect("toggled", self.toggleDNSCheckbox)
        self.checkboxGlobalDNS.connect("toggled", self.toggleGlobalDNSCheckbox)
        self.des = self.connect("destroy", self.destroycalled)

        # Start with all disabled, then they will be enabled later.
        self.checkboxStaticIP.set_active(False)
        self.checkboxStaticDNS.set_active(False)
    
    def destroycalled(self, *args):
        self.disconnect(self.des)
        super(NetworkEntry, self).destroy()
        self.destroy()[/php]
...
[php]class WiredNetworkEntry(NetworkEntry):
    # Creates the wired network expander.
    def __init__(self):
        NetworkEntry.__init__(self)
        self.set_label(language['wired_network'])
        self.resetStaticCheckboxes()
        self.comboProfileNames = gtk.combo_box_entry_new_text()
        self.isFullGUI = True

        self.profileList = config.GetWiredProfileList()
        if self.profileList:  # Make sure there is something in it...
            for x in config.GetWiredProfileList():  # Add all the names to the combobox
                self.comboProfileNames.append_text(x)
        self.hboxTemp = gtk.HBox(False, 0)
        hboxDef = gtk.HBox(False, 0)
        buttonAdd = gtk.Button(stock=gtk.STOCK_ADD)
        buttonDelete = gtk.Button(stock=gtk.STOCK_DELETE)
        self.profileHelp = gtk.Label(language['wired_network_instructions'])
        self.checkboxDefaultProfile = gtk.CheckButton(language['default_wired'])

        self.profileHelp.set_justify(gtk.JUSTIFY_LEFT)
        self.profileHelp.set_line_wrap(True)

        self.vboxTop.pack_start(self.profileHelp, fill=True, expand=True)
        self.hboxTemp.pack_start(self.comboProfileNames, fill=True, expand=True)
        self.hboxTemp.pack_start(buttonAdd, fill=False, expand=False)
        self.hboxTemp.pack_start(buttonDelete, fill=False, expand=False)
        hboxDef.pack_start(self.checkboxDefaultProfile, fill=False, expand=False)

        buttonAdd.connect("clicked", self.addProfile)
        buttonDelete.connect("clicked", self.removeProfile)
        self.comboProfileNames.connect("changed", self.changeProfile)
        self.scriptButton.connect("button-press-event", self.editScripts)
        self.vboxTop.pack_start(hboxDef)
        self.vboxTop.pack_start(self.hboxTemp)

        if stringToBoolean(wired.GetWiredProperty("default")):
            self.checkboxDefaultProfile.set_active(True)
        else:
            self.checkboxDefaultProfile.set_active(False)
        self.checkboxDefaultProfile.connect("toggled", self.toggleDefaultProfile)

        self.show_all()
        self.profileHelp.hide()
        if self.profileList != None:
            prof = config.GetDefaultWiredNetwork()
            if prof != None:  # Make sure the default profile gets displayed.
                i = 0
                while self.comboProfileNames.get_active_text() != prof:
                    self.comboProfileNames.set_active(i)
                    i += 1
            else:
                self.comboProfileNames.set_active(0)
            print "wired profiles found"
            self.set_expanded(False)
        else:
            print "no wired profiles found"
            if not wired.GetAlwaysShowWiredInterface():
                self.set_expanded(True)
            self.profileHelp.show()
        self.des2 = self.connect("destroy", self.destroycalled)

    def destroycalled(self, *args):
        self.disconnect(self.des2)
        super(WiredNetworkEntry, self).destroycalled()
        self.destroy()[/php]
...
[php]class WirelessNetworkEntry(NetworkEntry):
    # This class is respsponsible for creating the expander
    # in each wirelessnetwork entry.
    def __init__(self, networkID):
        self.networkID = networkID
        # Create the data labels
        NetworkEntry.__init__(self)
        self.essid = wireless.GetWirelessProperty(networkID, "essid")
        print "ESSID : " + self.essid
        self.set_label(self.essid)

        # Make the vbox to hold the encryption stuff.
        self.vboxEncryptionInformation = gtk.VBox(False, 0)
        # Make the combo box.
        self.comboEncryption = gtk.combo_box_new_text()
        self.checkboxEncryption = gtk.CheckButton(language['use_encryption'])
        self.lblStrength = GreyLabel()
        self.lblEncryption = GreyLabel()
        self.lblMAC = GreyLabel()
        self.lblChannel = GreyLabel()
        self.lblMode = GreyLabel()
        self.hboxStatus = gtk.HBox(False, 5)
        self.checkGlobalSettings = gtk.CheckButton(language['global_settings'])
        self.checkboxAutoConnect = gtk.CheckButton(language['automatic_connect'])
        self.checkboxAutoConnect.connect("toggled", self.updateAutoConnect)

        self.hboxStatus.pack_start(self.lblStrength, fill=False, expand=True)
        self.hboxStatus.pack_start(self.lblEncryption, fill=False, expand=True)
        self.hboxStatus.pack_start(self.lblMAC, fill=False, expand=True)
        self.hboxStatus.pack_start(self.lblMode, fill=False, expand=True)
        self.hboxStatus.pack_start(self.lblChannel, fill=False, expand=True)

        self.vboxTop.pack_start(self.checkboxAutoConnect, fill=False, 
                                expand=False)
        self.vboxTop.pack_start(self.hboxStatus, fill=True, expand=True)
        
        self.vboxAdvanced.pack_start(self.checkGlobalSettings, fill=False,
                                     expand=False)
        
        self.vboxAdvanced.pack_start(self.checkboxEncryption, fill=False,
                                     expand=False)

        self.txtIP.set_text(self.format_entry(networkID,"ip"))
        self.txtNetmask.set_text(self.format_entry(networkID,"netmask"))
        self.txtGateway.set_text(self.format_entry(networkID,"gateway"))

        if wireless.GetWirelessProperty(networkID,'use_global_dns'):
            self.checkboxGlobalDNS.set_active(True)

        if wireless.GetWirelessProperty(networkID, "dns1") != None:
            self.txtDNS1.set_text(self.format_entry(networkID, "dns1"))

        if wireless.GetWirelessProperty(networkID, 'dns2') != None:
            self.txtDNS2.set_text(self.format_entry(networkID, "dns2"))

        if wireless.GetWirelessProperty(networkID, 'dns3') != None:
            self.txtDNS3.set_text(self.format_entry(networkID, "dns3"))

        self.resetStaticCheckboxes()
        encryptionTypes = misc.LoadEncryptionMethods()

        self.checkboxEncryption.set_active(False)
        self.comboEncryption.set_sensitive(False)

        if stringToBoolean(self.format_entry(networkID, "automatic")):
            self.checkboxAutoConnect.set_active(True)
        else:
            self.checkboxAutoConnect.set_active(False)
            
        # Set it up right, with disabled stuff
        self.toggleEncryption()

        # Add the names to the menu
        activeID = -1  # Set the menu to this item when we are done
        for x in encryptionTypes:
            self.comboEncryption.append_text(encryptionTypes[x][0])
            if encryptionTypes[x][1] == wireless.GetWirelessProperty(networkID,
                                                                     "enctype"):
                activeID = x

        self.comboEncryption.set_active(activeID)
        if activeID != -1:
            self.checkboxEncryption.set_active(True)
            self.comboEncryption.set_sensitive(True)
            self.vboxEncryptionInformation.set_sensitive(True)
        else:
            self.comboEncryption.set_active(0)

        self.vboxAdvanced.pack_start(self.comboEncryption)
        self.vboxAdvanced.pack_start(self.vboxEncryptionInformation)
        self.changeEncryptionMethod()
        self.scriptButton.connect("button-press-event", self.editScripts)
        self.checkboxEncryption.connect("toggled", self.toggleEncryption)
        self.comboEncryption.connect("changed", self.changeEncryptionMethod)
        self.show_all()
        self.wifides = self.connect("destroy", self.destroycalled)

    def destroycalled(self, *args):
        self.disconnect(self.wifides)
        self.destroy()
        super(WirelessNetworkEntry, self).destroycalled()[/php]

I added the destroycalled/destroy_event methods as part of my debugging effort.  I've put all sorts of stuff in those to try to fix the leak (trying to destroy all the objects in the class individually, etc.) but no luck.  The one thing I did notice is that the reference count on the PrettyNetworkEntry class was one higher than it should have been when it got destroyed, but I took care of that with the self.expander.higherLevel stuff in the PrettyNetworkEntry destroycalled method.

Here's the code in refresh_networks of note
[php]    def refresh_networks(self, widget=None, fresh=True, hidden=None):
        """ Refreshes the network list.
        
        If fresh=True, scans for wireless networks and displays the results.
        If a ethernet connection is available, or the user has chosen to,
        displays a Wired Network entry as well.
        If hidden isn't None, will scan for networks after running
        iwconfig <wireless interface> essid <hidden>.
        
        """
        print "refreshing..."
        printLine = False  # We don't print a separator by default.
        # Remove stuff already in there. ***This isn't working right ***
        for z in self.network_list:
            self.network_list.remove(z)
            z.destroy()
            print 'ref count ' + str(sys.getrefcount(z))
            del z

        if wired.CheckPluggedIn() or wired.GetAlwaysShowWiredInterface():
            printLine = True  # In this case we print a separator.
            wirednet = PrettyWiredNetworkEntry()
            self.network_list.pack_start(wirednet, fill=False, expand=False)
            wirednet.connectButton.connect("button-press-event", self.connect,
                                           "wired", 0, wirednet)
            wirednet.expander.advancedButton.connect("button-press-event",
                                                     self.edit_advanced,
                                                     "wired", 0, wirednet)
        ....

        instructLabel = self.wTree.get_widget("label_instructions")
        if num_networks > 0:
            for x in range(0, num_networks):
                    if printLine:
                        sep = gtk.HSeparator()
                        self.network_list.pack_start(sep, padding=10, expand=False,
                                                     fill=False)
                        sep.show()
                    else:
                        printLine = True
                    tempnet = PrettyWirelessNetworkEntry(x)
                    tempnet.show_all()
                    self.network_list.pack_start(tempnet, expand=False, fill=False)
                    tempnet.connectButton.connect("button-press-event",
                                                   self.connect, "wireless", x,
                                                   tempnet)
                    tempnet.expander.advancedButton.connect("button-press-event",
                                                            self.edit_advanced,
                                                            "wireless", x, tempnet)
        else:
            ...[/php]I didn't write most of this particular file (and only a few lines of the code I'm posting here), so I can't really speak for any of the design decisions.  Eventually I think we'll end up refactoring this to fix the variable names, and maybe rewrite the whole thing altogether.  But in the meantime, any help anyone could give would be hugely appreciated.  And if you need more info, just let me know.

---

### Post by imdano on 2008-02-26
I guess I'll bump this one up.  It's probably a little bit too complicated a problem to ask about here, since I think it'd take a while to figure out what's going on with the code, aside from trying to spot the leak.

---

