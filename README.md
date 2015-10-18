	system:
		hplip: https://bugs.launchpad.net/hplip/+bug/1442734
		add network-manager-openvpn-gnome
		add mmcblk support (so we can install on sd card)?
		ubiquity: crypted swap: http://forums.linuxmint.com/viewtopic.php?f=90&t=201025#p1050041
			replace
				# Add crypttab entry
				echo “cryptswap$i UUID=$uuid /dev/urandom swap,cipher=aes-cbc-essiv:sha256″ >> /etc/crypttab
			with
				# Add crypttab entry
				echo “cryptswap$i UUID=$uuid /dev/urandom swap,offset=8,cipher=aes-cbc-essiv:sha256″ >> /etc/crypttab
			without “offset=8″, a freshly installed Linuxmint finds the cryptswap and then destroys its UUID. On reboot, the UUID is gone and the swap partition cannot be found anymore. The offset should fix that problem.
		ubiquity: select fastest repositories based on location
		check if libgtkmm-2.4-1c2a should be installed (reported missing in Cinnamon 17.1 32-bit). Missing lib creates problems for VMware Player (missing menus) and changing Themes.
		integrate nemo-preview
		ship with nemo extensions, disable them by default (using overrides)
		restore menubar in terminals
		MATE/Xfce: provide QT5 override in /etc/X11/Xsession.d to make it use GTK style

	apps:
		vlc: upgrade to 2.2. It supports HEVC/h265 (same quality at half the file size). PPA available at ppa:mc3man/trusty-media
		gnome-terminal/mate-terminal: bring back menubar by default

	cinnamon:
		default settings:
			window-list thumbs?
			attached dialogs?
		bugs:
			nemo: Rename bug disables copy and paste https://github.com/linuxmint/nemo/issues/909
			quassel indicator doesn't show on login, or on 2nd launch
			Resized the panel a couple times, turned of "Use customized panel size" and crash

	mate:
		alt-tab thumbs cost perf..
		1.12: marco: center windows by default (was changed to false in git master)
		caja: clicking on home [compact view] in sidebar then on filesystem [icon view], back and forth, eventually dir names disappear
		make transitional packages for:
			mate-dialogs -> zenity
			mate-calc -> gcaltool
			mate-system-tools -> gnome-system-tools
		some panel applets get wrong positions when resolution changes https://github.com/mate-desktop/mate-panel/issues/84

	xfce:
		the xfce4-whiskermenu-plugin is not installed through the meta-package
		exo-utils can't open paths with special chars in them: http://forums.linuxmint.com/viewtopic.php?f=47&t=202069

	kde:
		mint kde 17.2 with asus ux303LA. On HDMI, can't clone screens, can't play sounds on tv. Both problems are solved by installing kde-workspace-randr. See https://bugs.launchpad.net/ubuntu/+source/kscreen/+bug/1213753 for details.

	mintdesktop
		support compiz current-viewport setting https://bitbucket.org/ubuntu-mate/mate-tweak/commits/77cf0249efa723e8dca58db4905bd71745bdb690

	mintupdate
		have two delays, one for initial update, and one for successive ones. That way we can reduce the initial one and increase the other.
		float division by zero when size of package is 0
		warn user when mirror is out of date

	mintbackup:
		consider using another alternative?

	mintsources:
		check that the added PPA supports the base codename (trusty for instance)
		prefer local mirrors
		window too wide in russian locale

	mintwelcome:
		point to mintdrivers

	mintdrivers:
		update APT cache prior to checking drivers

	mintupload:
		ftps support

	mintlocale:
		either hide im-config or have the menu item launch mintlocale's IM setup

	lmde:
		update grub (improves efi support)
		Add va-driver-all to the list of installed packages (fixes black bands with Intel GPUs).
		upgrade path:
			/etc/plymouth/plymouthd.conf -->  [Daemon]  Theme=mint-logo
			logind.conf
		history and completion in bashrc
		betsy, meld 3.12.1 doesn't work (shows a black background), upgrade it to 3.12.3
		install libhal1-flash by default
		consider activating http://backports.debian.org/changes/jessie-backports.html

	website:
		switch sensitive parts to https (md5 in particular)
		Update tapatalk API on forums.

	PIA:
		command to set up connection
		ca.crt
		tutorial
		support for openvpn
