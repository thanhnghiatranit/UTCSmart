# UTCSmart
<tbody>
					<%
						//Lấy ra danh sách sản phẩm
					MSTCUSTOMER_DAO dao=new MSTCUSTOMER_DAO();
					//List<MSTCUSTOMER> list = dao.GetCustomerPT(first, last);
					//MSTCUSTOMER_DAO dao=new MSTCUSTOMER_DAO();
					ArrayList<MSTCUSTOMER> list = new ArrayList<>();
					if(request.getParameter("action").equals("search")){
						System.out.println("Zooo");
						String name = request.getParameter("name");
						String sex = request.getParameter("sex");
						String birthday1 = request.getParameter("bd1");
						String birthday2 = request.getParameter("bd2");
						list = dao.getSearch(name, sex, birthday1, birthday2);
					}else{
						list = dao.getListCustomer();
					}
						for (MSTCUSTOMER customerlist : dao.getListCustomer()) {
					%>
					<tr>
						
					
						<td><input type="checkbox"
							id="<%=customerlist.getS_customerID()%>"
							value="<%=customerlist.getS_customerID()%>"
							onclick="
							checkedFunction(this)" name="check_list"
							class="styled"></td>


						<td><a
							href="T003.jsp?action=view&idCustomer=<%=customerlist.getS_customerID()%>"><%=(customerlist.getS_customerID() != null ? customerlist.getS_customerID() : "")%></a></td>
						<td><%=(customerlist.getS_customerName() != null ? customerlist.getS_customerName() : "")%></td>
						<td><%=(customerlist.getS_sex() != null ? customerlist.getS_sex() : "")%></td>
						<td><%=(customerlist.getS_birthday() != null ? customerlist.getS_birthday() : "")%></td>
						<td><%=(customerlist.getS_address() != null ? customerlist.getS_address() : "")%></td>
					</tr>
				</tbody>
				<%
					}
				%>
			</table>
