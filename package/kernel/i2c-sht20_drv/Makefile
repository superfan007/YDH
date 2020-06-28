#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=i2c-sht20_drv
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define KernelPackage/i2c-sht20_drv
  SUBMENU:=Other modules
  TITLE:=sht20 i2c support
  DEPENDS:= +kmod-i2c-core
  FILES:=$(PKG_BUILD_DIR)/i2c-sht20_drv.ko
endef

define KernelPackage/wrt55agv2-spidevs/description
  Kernel module for the SPI devices on the WRT55AG v2 board.
endef

MAKE_OPTS:= \
	ARCH:="$(LINUX_KARCH)" \
	CROSS_COMPILE:="$(TARGET_CROSS)" \
	SUBDIRS:="$(PKG_BUILD_DIR)"
	TITLE:=Sht20 driver
	FILES:=$(PKG_BUILD_DIR)/i2c-sht20_drv.ko
define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile
	$(MAKE) -C "$(LINUX_DIR)" \
		$(MAKE_OPTS) \
		modules
endef

$(eval $(call KernelPackage,i2c-sht20_drv))
