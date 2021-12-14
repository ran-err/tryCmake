cmake_minimum_required(VERSION 3.19)
project(tryCmake)

set(CMAKE_CXX_STANDARD 20)

#add_executable(main main.cpp)
#add_executable(second second.cpp)

# 当前工作路径，即CMakeList.txt所在的文件夹
message(Working\ Directory:\ ${CMAKE_CURRENT_SOURCE_DIR})
# 获取cpp文件相对于当前工作路径CMAKE_CURRENT_SOURCE_DIR的相对路径，即文件名
file (GLOB files RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)
# 遍历每个文件名
foreach (file ${files})
    # 输出文件名
    message(${file})
    # 将去掉后缀的文件名存入exe变量（executable的缩写，不是代表.exe）
    string(REGEX REPLACE "(.+).cpp$" "\\1" exe ${file})
    # 分别生成add_executable(<name> <source>)命令
    add_executable (${exe} ${file})
    message(add_executable(${exe}\ ${file}))
endforeach ()