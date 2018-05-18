<p align="center">
<img src="https://github.com/TheAssassin/AppImageLauncher/raw/master/resources/doc/screenshot.png"/>
</p>

# AppImageLauncher

AppImageLauncher makes your Linux desktop AppImage ready™. By installing it, you won't ever have to worry about AppImages again. You can always double click them without making them executable first, just like you should be able to do nowadays. You can integrate AppImages with a single mouse click, and manage them from your application launcher. Updating and removing AppImages becomes as easy as never before.

Due to its simple but efficient way to integrate into your system, it plays well with other applications that can be used to manage AppImages, for example app stores. However, it doesn't depend on any of those, and can run completely standalone.

Install AppImageLauncher today for your distribution and enjoy using AppImages as easy as never before!
 

## About the project

AppImages and Linux desktops, that's two things which don't work together very well currently. Since AppImages are normal executables, it'd suffice if desktop environments like KDE, GNOME, Xfce, ... would assist users in making those files executable, but as we learned recently, some desktop environments consider this a security risk, and want to force users to use app stores.

Being executable isn't really all that is needed to provide a good desktop experience. AppImages should be accessible from the application menus and launchers. This so-called "desktop integration" can't be provided by the AppImages themselves even though some AppImages ship with a "desktop integration script" prompting the user to integrate the AppImages, as there's too many impliciations that require an external software, especially regarding the cleanup and removal of AppImages. Also, if applications are simply made executable, they're still spread all over the users' personal files and folders. The average user doesn't necessarily like a Downloads directory that is full of AppImages with cryptic filenames.

Therefore, new, system-side solutions have been developed to perform the desktop integration. The oldest available solution is [appimaged](https://github.com/AppImage/AppImageKit), a daemon users can install that performs everything in the background, automagically, without notifying the user in any way. It scans a predefined set of directories including `~/Downloads` and `~/.bin`, makes AppImages which are found executable and performs the desktop integration. This is rather inefficient, as appimaged's operations and monitoring produce a lot of file I/O. Also, many users don't like the lack of control.

A new solution for native AppImage support has been developed: AppImageLauncher. AppImageLauncher integrates deeply in the system and intercepts all attempts to open an AppImage, becoming the first instance to handle all AppImage invocations.

Being the launcher for AppImages, AppImageLauncher can control how the system treats AppImages. It can perform the desktop integration, AppImage removal (also called "uninstallation" sometimes, but as AppImages are not really installed, this term doesn't fit very well), and could be used for many other tasks in the future, like update checks and alike.


## Articles about AppImageLauncher

A few articles have been written about AppImageLauncher already:

  - https://www.linuxuprising.com/2018/04/easily-run-and-integrate-appimage-files.html (English)
  - http://linux-os.net/appimagelauncher-ejecuta-e-integra-facilmente-aplicaciones-en-appimage/ (Spanish)
    - same article also available here: https://blog.desdelinux.net/appimagelauncher-ejecuta-e-integra-facilmente-aplicaciones-en-appimage/
  - http://www.edivaldobrito.com.br/integrador-appimagelauncher-no-linux/ (Portuguese)


## Installation

### System wide Installation

AppImageLauncher is supposed to integrate deeply in the systems. Therefore, an installation via native system packages is the preferred way to install AppImageLauncher. This way, AppImageLauncher's package can perform the necessary steps to have your system use it for all AppImage invocations.

AppImageLauncher is built on Ubuntu trusty. The Debian and RPM packages provided on the [release page](https://github.com/TheAssassin/AppImageLauncher/releases) are tested on the following platforms:

  - Ubuntu trusty (14.04) and newer
    - **Important:** Ubuntu bionic (and newer) broke with the backwards compatibility of its `libcurl` packages, therefore users of these systems need to install the special `bionic` package
  - Debian stable (jessie, 8) and newer
  - Netrunner 17 and newer
  - openSUSE Leap 42 and newer
  - openSUSE Tumbleweed

The installation of packages on systems with a set of packages similar to one of the listed ones (e.g., Linux Mint, Fedora, etc.) should work as well.

Arch Linux, Manjaro, Antergos and Netrunner Rolling users can use AUR to install AppImageLauncher by installing [appimagelauncher-git](https://aur.archlinux.org/packages/appimagelauncher-git) (thanks @NuLogicSystems for setting up the build).


### AppImage

For evaluation purposes, you can download an AppImage from the [release page](https://github.com/TheAssassin/AppImageLauncher/releases), which will demonstrate how AppImageLauncher works. Please beware that certain features, like the removal of AppImages, require AppImageLauncher to be installed system wide.


## How it works

AppImageLauncher is responsible for the desktop integration. When the user launches an AppImage, the software checks whether the AppImage has been integrated already. If not, it displays a dialog prompting the user whether to run the AppImage once, or move it to a predefined location and adding it to the application menus, launchers, etc.


## Technical background information

Details about how AppImageLauncher registers itself in the system can be found on [this Wiki page](https://github.com/TheAssassin/AppImageLauncher/wiki/Idea).
