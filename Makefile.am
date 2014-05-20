cfgdir		  = $(datadir)/vyatta-cfg/templates
opdir		  = $(datadir)/vyatta-op/templates
share_perl5dir	  = $(datarootdir)/perl5/Vyatta
bin_sudo_usersdir = $(bindir)/sudo-users
curverdir         = $(sysconfdir)/config-migrate/current
templatedir       = /opt/vyatta/etc


template_DATA = etc/pptp-provider-template

cpiop = find  . ! -regex '\(.*~\|.*\.bak\|.*\.swp\|.*\#.*\#\)' -print0 | \
  cpio -0pd

install-exec-hook:
	mkdir -p $(DESTDIR)$(cfgdir)
	cd templates-cfg; $(cpiop) $(DESTDIR)$(cfgdir)
	mkdir -p $(DESTDIR)$(opdir)
	cd templates-op; $(cpiop) $(DESTDIR)$(opdir)
	mkdir -p $(DESTDIR)/etc/ppp/ip-pre-up.d
	cp sysconf/rename-pptpc $(DESTDIR)/etc/ppp/ip-pre-up.d/9998rename-pptpc
	chmod 755 $(DESTDIR)/etc/ppp/ip-pre-up.d/9998rename-pptpc
