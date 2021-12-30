<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
pageEncoding="ISO-8859-1"%>
<%@page import="java.sql.*,java.util.*,java.io.*"%>
<%
try{
String username=request.getParameter("username");
String password=request.getParameter("password");
String mail=request.getParameter("mail");
Class.forName("com.mysql.jdbc.Driver");
Connection conn=DriverManager.getConnection("jdbc:mysql://127.0.0.1:3306/login","root","");
PreparedStatement ps=conn.prepareStatement("insert into log values(?,?,?)");
ps.setString(1,username);
ps.setString(2,password);
ps.setString(3,mail);
ps.executeUpdate();
out.println("Record Inserted Successfully...!");
ps.close();
conn.close();
}
catch(Exception e)
{out.println(e);
}
%>