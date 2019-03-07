###### EDIT #####################
# Directory with ui and resource files, without trailing SLASH
RESOURCE_DIR = designer

# Directory for compiled resources (RELATIVE TO src/), without trailing SLASH
COMPILED_DIR = {{cookiecutter.package_name}}/gui

# UI files to compile, separated by SPACE
UI_FILES = mainwindow.ui
# Qt resource files to compile, separated by SPACE
QRC_FILES = resources.qrc

# pyuic5 and pyrcc5 binaries
PYUIC = pyuic5
PYRCC = pyrcc5

#################################
# DO NOT EDIT FOLLOWING

IMPORT_FROM = $(subst /,.,$(COMPILED_DIR))
COMPILED_UI = $(UI_FILES:%.ui=$(COMPILED_DIR)/%.py)
COMPILED_RESOURCES = $(QRC_FILES:%.qrc=$(COMPILED_DIR)/%_rc.py)

all : resources ui

resources : $(COMPILED_RESOURCES)

ui : $(COMPILED_UI)

$(COMPILED_DIR)/%.py : $(RESOURCE_DIR)/%.ui
	$(PYUIC) $< -o $@ --import-from=$(IMPORT_FROM)

$(COMPILED_DIR)/%_rc.py : $(RESOURCE_DIR)/%.qrc
	$(PYRCC) $< -o $@

clean :
	$(RM) $(COMPILED_UI) $(COMPILED_RESOURCES) $(COMPILED_UI:.py=.pyc) $(COMPILED_RESOURCES:.py=.pyc)
