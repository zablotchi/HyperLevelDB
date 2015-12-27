CC=cc
CXX=g++
PLATFORM=OS_LINUX
PLATFORM_LDFLAGS= -lpthread -lrt -lgflags -lz -lbz2 -ltcmalloc
JAVA_LDFLAGS= -lpthread -lrt -lz -lbz2 -ltcmalloc
JAVA_STATIC_LDFLAGS= -lpthread -lrt
VALGRIND_VER=
PLATFORM_CCFLAGS= -DROCKSDB_PLATFORM_POSIX -DROCKSDB_LIB_IO_POSIX  -DOS_LINUX -fno-builtin-memcmp -DROCKSDB_FALLOCATE_PRESENT -DGFLAGS=google -DZLIB -DBZIP2 -DROCKSDB_MALLOC_USABLE_SIZE -march=native 
PLATFORM_CXXFLAGS=-std=c++11  -DROCKSDB_PLATFORM_POSIX -DROCKSDB_LIB_IO_POSIX  -DOS_LINUX -fno-builtin-memcmp -DROCKSDB_FALLOCATE_PRESENT -DGFLAGS=google -DZLIB -DBZIP2 -DROCKSDB_MALLOC_USABLE_SIZE -march=native 
PLATFORM_SHARED_CFLAGS=-fPIC
PLATFORM_SHARED_EXT=so
PLATFORM_SHARED_LDFLAGS=-Wl,--no-as-needed -shared -Wl,-soname -Wl,
PLATFORM_SHARED_VERSIONED=true
EXEC_LDFLAGS=
JEMALLOC_INCLUDE=
JEMALLOC_LIB=
ROCKSDB_MAJOR=4
ROCKSDB_MINOR=4
ROCKSDB_PATCH=0
CLANG_SCAN_BUILD=scan-build
CLANG_ANALYZER=

CFLAGS += -I.. -I../include -I../db/atomic_ops -I../db/ascylib_aux -I../db/ascylib_external/include $(PLATFORM_CCFLAGS) $(OPT)
CXXFLAGS += -I.. -I../include -I../db/atomic_ops -I../db/ascylib_aux -I../db/ascylib_external/include $(PLATFORM_CXXFLAGS) $(OPT)

include Makefile.common.ascylib

.PHONY: clean libhyperleveldb

simple_example: libhyperleveldb simple_example.cc
	# $(CXX) $(CXXFLAGS) $@.cc -o $@ ../libhyperleveldb.la -I../include -O2 -std=c++11 $(PLATFORM_LDFLAGS) $(PLATFORM_CXXFLAGS) $(EXEC_LDFLAGS)
	libtool --mode=link	$(CXX) $(CXXFLAGS) $@.cc -o $@ ../libhyperleveldb.la -I../include -O2 -std=c++11 $(PLATFORM_LDFLAGS) $(PLATFORM_CXXFLAGS) $(EXEC_LDFLAGS)

clean:
	rm -rf ./simple_example

reconf:
	cd .. && autoreconf -i && ./configure

libhyperleveldb:
	cd .. && make
