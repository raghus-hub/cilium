include ../../Makefile.defs

all: cilium-cni

TARGET=cilium-cni

clean:
	go clean
	rm -f $(TARGET)

SOURCES := $(shell find ../../api/v1/models ../../common ../../pkg/client ../../pkg/endpoint . -name '*.go')

$(TARGET): $(SOURCES)
	go build $(GOBUILD) -o $(TARGET) ./cilium-cni.go

install:
	$(INSTALL) -m 0755 -d $(DESTDIR)/etc/cni/net.d
	$(INSTALL) -m 0644 10-cilium-cni.conf $(DESTDIR)/etc/cni/net.d
	$(INSTALL) -m 0755 -d $(DESTDIR)/opt/cni/bin
	$(INSTALL) -m 0755 $(TARGET) $(DESTDIR)/opt/cni/bin
