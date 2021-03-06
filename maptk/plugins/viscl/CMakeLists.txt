# Build / install plugin containing VisCL algorithm implementations + support
# structures

set( maptk_viscl_headers_public
  convert_image.h
  descriptor_set.h
  detect_features.h
  extract_descriptors.h
  feature_set.h
  image_container.h
  match_features.h
  match_set.h
  register_algorithms.h
  utils.h
  )
kwiver_install_headers(
  SUBDIR     maptk/plugins/viscl
  ${maptk_viscl_headers_public}
  )
kwiver_install_headers(
  ${CMAKE_CURRENT_BINARY_DIR}/maptk_viscl_export.h
  NOPATH   SUBDIR     maptk/plugins/viscl
  )

set( maptk_viscl_sources
  convert_image.cxx
  descriptor_set.cxx
  detect_features.cxx
  extract_descriptors.cxx
  feature_set.cxx
  image_container.cxx
  match_features.cxx
  match_set.cxx
  register_algorithms.cxx
  utils.cxx
  )
kwiver_add_library( maptk_viscl
  ${maptk_viscl_headers_public}
  ${maptk_viscl_sources}
  )
target_link_libraries( maptk_viscl
  PUBLIC               maptk
                       viscl_core
                       viscl_tasks
                       viscl_vxl
  )
maptk_create_plugin( maptk_viscl
  algorithm_plugin_interface.cxx
  )
