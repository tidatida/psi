# Howto build Psi using cmake utility

## Prepare sources:

> $ mkdir build && cd build
> $ cmake FLAGS ..

  instead of FLAGS can be the flags from "Usefull CMAKE FLAGS" section

## Build sources:

> $ cmake --build . --target all --

or

> $ make

## Install Psi+:

> $ cmake --build . --target install --

or

> $ make install

## Usefull CMAKE FLAGS:

>  -DUSE_QT5=ON

  to build psi-plus with Qt5 support (default ON)

> -DCMAKE_INSTALL_PREFIX=prefix

  to set installation prefix

>  -DBUNDLED_IRIS=ON

  to build iris library bundled (default ON)

>  -DUSE_ENCHANT=ON

  to use Enchant spellchecker (default OFF)

>  -DUSE_HUNSPELL=ON

  to use Hunspell spellchecker (default ON)

>  -DSEPARATE_QJDNS=ON

  to build qjdns library as separate library (default ON)

>  -DPSI_PLUS_VERSION=${version}

  to set Psi-plus version manually (in format x.xx.xxx.xxx, where x is a decimal digit). Script sets this flag automatically from "version" file if it exists in psi-plus directory

>  -DCMAKE_BUILD_TYPE=Release (default: Release)

  to set build type. Possible values: DEBUG, RELEASE, RELWITHDEBINFO, MINSIZEREL

> -USE_CCACHE=ON (default: ON)

  to enable ccache utility support

>  -DUSE_MXE=ON (default: OFF)

  Enables MXE (M cross environment) support. Disables USE_CCACHE, adds new dependencies if PRODUCTION flag is enabled

> -DENABLE_PLUGINS=ON

  to build psi-plus plugins (default OFF)

>  -DONLY_PLUGINS=ON

  to build only psi-plus plugins (default OFF). On enabling this flag ENABLE_PLUGINS flag turns on automatically

## Work with plugins:

### Next flags are working only if ENABLE_PLUGINS or ONLY_PLUGINS are enabled

>  -DBUILD_PLUGINS=${plugins}

  set list of plugins to build. To build all plugins:  -DBUILD_PLUGINS="ALL" or do not set this flag

  - possible values for ${plugins}:

    historykeeperplugin	stopspamplugin juickplugin translateplugin gomokugameplugin attentionplugin
    cleanerplugin autoreplyplugin contentdownloaderplugin	qipxstatusesplugin skinsplugin icqdieplugin
    clientswitcherplugin captchaformsplugin watcherplugin videostatusplugin screenshotplugin
    jabberdiskplugin storagenotesplugin	extendedoptionsplugin imageplugin	extendedmenuplugin
    birthdayreminderplugin gmailserviceplugin gnupgplugin pepchangenotifyplugin otrplugin
    chessplugin conferenceloggerplugin gnome3supportplugin enummessagesplugin httpuploadplugin 
    imagepreviewplugin

  Example:

  > -DBUILD_PLUGINS="chessplugin;otrplugin;gnome3supportplugin"


>  -DPLUGINS_PATH=${path} 

  to install plugins into ${path}. To install into default suffix:

  -DPLUGINS_PATH=lib/psi-plus/plugins or do not set this flag

  For example to install plugins into ~/.local/share/psi+/plugins:

  > -DCMAKE_INSTALL_PREFIX=$HOME/.local -DPLUGINS_PATH=share/psi+/plugins

  For example to install plugins into /usr/share/psi-plus/plugins:

  > -DCMAKE_INSTALL_PREFIX=/usr -DPLUGINS_PATH=share/psi-plus/plugins

## Win32 or MXE Section:

>  -DQCA_DIR=DIRECTORY

  to set Qca library root directory

>  -DIDN_ROOT=DIRECTORY

  to set Idn library root directory

>  -DZLIB_ROOT=DIRECTORY

  to set Zlib library root directory

>  -DHUNSPELL_ROOT=DIRECTORY

  to set Hunspell library root directory

>  -DPRODUCTION=ON

  to install needed libs to run Psi+. When you running cmake from MXE you also need to enable USE_MXE flag

> -DBUILD_ARCH=i386 (default: i386 for MinGW and win32 for MSVC)

  to set build architecture. Possible values: i386, x86_64 for MinGW and win32, win64 for MSVC

### To build OTRPLUGIN in OS WINDOWS you need to set additional variables

> -DLIBGCRYPT_ROOT=%LIBGCRYPT_ROOT%

  path to LIBGCRYPT library root directory

> -DLIBGPGERROR_ROOT=%LIBGPGERROR_ROOT%

  path to LIBGPG-ERROR library root directory

> -DLIBOTR_ROOT=%LIBOTR_ROOT%

  path to LIBOTR library root directory

> -DLIBTIDY_ROOT=%LIBTIDY_ROOT%

  path to LIBTIDY library root directory

  For example:

  > -DLIBGCRYPT_ROOT=C:\libgcrypt -DLIBGPGERROR_ROOT=C:\libgpg-error -DLIBOTR_ROOT=C:\libotr -DLIBTIDY_ROOT=C:\libtidy

### If you using Psi+ SDK you need to set SDK_PATH:

>  -DSDK_PATH=path

# TODO LIST:
- [ ] Add MacOSX support
