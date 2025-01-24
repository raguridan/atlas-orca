# (C) Copyright 2021- ECMWF.
#
# This software is licensed under the terms of the Apache Licence Version 2.0
# which can be obtained at http://www.apache.org/licenses/LICENSE-2.0.
#
# In applying this licence, ECMWF does not waive the privileges and immunities
# granted to it by virtue of its status as an intergovernmental organisation nor
# does it submit to any jurisdiction.

configure_file(version.cc.in version.cc)

ecbuild_add_library(
    TARGET atlas-orca
    TYPE SHARED
    SOURCES 
        Library.cc
        Library.h
        grid/Orca.cc
        grid/Orca.h
        grid/OrcaGrid.cc
        grid/OrcaGrid.h
        grid/OrcaGridBuilder.cc
        meshgenerator/OrcaMeshGenerator.cc
        meshgenerator/OrcaMeshGenerator.h
        util/AtlasIOReader.h
        util/ComputeCachedPath.h
        util/ComputeUid.h
        util/ComputeUid.cc
        util/DetectInvalidElements.h
        util/Download.h
        util/Enums.h
        util/Flag.h
        util/OrcaData.cc
        util/OrcaData.h
        util/OrcaDataFile.h
        util/OrcaPeriodicity.cc
        util/OrcaPeriodicity.h
        util/PointIJ.h
        ${CMAKE_CURRENT_BINARY_DIR}/version.cc
        version.h
    HEADER_DESTINATION "include/atlas-orca"
    PUBLIC_LIBS atlas
    PUBLIC_INCLUDES 
       $<INSTALL_INTERFACE:include/atlas-orca>
       $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/src>
       $<BUILD_INTERFACE:${PROJECT_BINARY_DIR}/src> )
