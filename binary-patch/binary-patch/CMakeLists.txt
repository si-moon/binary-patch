# binary-patch / binary-patch
project("binary-patch-binary-patch" CXX)
add_library("${PROJECT_NAME}" STATIC)
add_library("binary-patch::binary-patch" ALIAS "${PROJECT_NAME}")


target_sources(
	"${PROJECT_NAME}"
	PRIVATE
		"${CMAKE_CURRENT_LIST_DIR}/src/Cli.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/BinaryPatcher.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/EntryParser.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/Entry.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/HexUtil.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/Key.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/Mac.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/Main.c++"
		"${CMAKE_CURRENT_LIST_DIR}/src/Options.c++"
)


target_include_directories(
	"${PROJECT_NAME}"
	PUBLIC
		"${CMAKE_CURRENT_LIST_DIR}/include"
)


target_link_libraries(
	"${PROJECT_NAME}"
	PUBLIC
		binary-patch::rapidcsv
		cxxopts::cxxopts
		ooxi::exception
	PRIVATE
		binary-patch::defaults
)


add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/executable")
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/test/BinaryPatcherTest")
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/test/CliTest")
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/test/HexUtilTest")
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/test/KeyTest")
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/test/MacTest")
add_subdirectory("${CMAKE_CURRENT_LIST_DIR}/test/SearchTest")
